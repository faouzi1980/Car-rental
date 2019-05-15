<template>
  <section>
    <Navbar
      @sort="sort"
      @carTypeFilter="carTypeFilter"
      @transmissionFilter="transmissionFilter"
      @fuelFilter="fuelFilter"
    />
    <div class="searchBar columns">
      <div class="column">
        <div class="field">
          <p class="control has-icons-left">
            <flat-pickr
              v-model="selectedDay"
              :config="config"
              class="input"
              placeholder="Select date"
              name="date"
            ></flat-pickr>
            <span class="icon is-small is-left">
              <box-icon name="calendar-event" color="#c8c8c8"></box-icon>
            </span>
          </p>
        </div>
      </div>
      <div class="column">
        <div class="field">
          <p class="control has-icons-left">
            <input class="input" type="text" placeholder="Search">
            <span class="icon is-small is-left">
              <box-icon name="search" color="#c8c8c8"></box-icon>
            </span>
          </p>
        </div>
      </div>
    </div>
    <transition name="fade" mode="out-in">
      <div v-if="loading" class="loading" :key="1">
        <box-icon name="loader-alt" size="lg" animation="spin" color="#c8c8c8"></box-icon>
      </div>
      <div class="section" v-else :key="2">
        <ul>
          <li v-for="(car, index) in displayedCars" :key="index">
            <CarCard :data="car" :day="selectedDay"/>
          </li>
        </ul>
        <div class="buttons has-addons">
          <span
            class="button"
            v-for="(pageNumber, key) in pages"
            @click="page = pageNumber"
            :key="key"
            :class="{'is-primary':page == pageNumber}"
          >{{pageNumber}}</span>
        </div>
      </div>
    </transition>
  </section>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import CarCard from "@/components/CarCard.vue";
import flatPickr from "vue-flatpickr-component";
import "flatpickr/dist/flatpickr.css";
import axios from "axios";
export default {
  props: ["day"],
  components: {
    Navbar,
    CarCard,
    flatPickr
  },
  data() {
    return {
      selectedPage: undefined,
      loading: false,
      cars: [],
      apiUrl: "https://api.sheety.co/311576ae-321a-43e3-9a5b-61b3ac373d85",
      page: 1,
      perPage: 6,
      pages: [],
      allCars: [],
      search: "",
      selectedDay: this.day,
      config: {
        minDate: "today"
      }
    };
  },
  methods: {
    countPages() {
      let numberOfPages = Math.ceil(this.cars.length / this.perPage);
      for (var i = 1; i <= numberOfPages; i++) {
        this.pages.push(i);
      }
    },
    sort(type) {
      this.pages = [];
      if (type == "low") {
        this.cars.sort(function(a, b) {
          var keyA = a.price,
            keyB = b.price;
          if (keyA < keyB) return -1;
          if (keyA > keyB) return 1;
          return 0;
        });
      } else {
        this.cars.sort(function(a, b) {
          var keyA = a.price,
            keyB = b.price;
          if (keyA > keyB) return -1;
          if (keyA < keyB) return 1;
          return 0;
        });
      }
    },
    carTypeFilter(type) {
      this.pages = [];
      this.cars = this.allCars;
      if (type != "All") {
        var carType = this.cars.filter(function(car) {
          return car.car_Type == type;
        });
        this.cars = carType;
      }
    },
    transmissionFilter(type) {
      this.pages = [];
      this.cars = this.allCars;
      if (type != "All") {
        var carType = this.cars.filter(function(car) {
          return car.transmission == type;
        });
        this.cars = carType;
      }
    },
    fuelFilter(type) {
      this.pages = [];
      this.cars = this.allCars;
      if (type != "All") {
        var carType = this.cars.filter(function(car) {
          return car.fuel_Type == type;
        });
        this.cars = carType;
      }
    },
    processCars(cars) {
      let page = this.page;
      let perPage = this.perPage;
      let from = page * perPage - perPage;
      let to = page * perPage;
      return cars.slice(from, to);
    },
    getCars() {
      this.loading = true;
      axios
        .get(this.apiUrl)
        .then(response => {
          console.log("Done");
          response.data.forEach(item => {
            this.cars.push(item);
            this.allCars.push(item);
          });
          this.loading = false;
        })
        .catch(error => {
          this.loading = true;
        });
    }
  },
  watch: {
    cars() {
      this.countPages();
    }
  },
  mounted() {
    this.getCars();
  },
  computed: {
    displayedCars() {
      return this.processCars(this.cars);
    }
  }
};
</script>


<style scoped>
.searchBar {
  padding: 16px;
}

.section {
  padding: 1.5rem;
}
.loading {
  height: 75vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

li {
  box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.14),
    0 3px 1px -2px rgba(0, 0, 0, 0.12), 0 1px 5px 0 rgba(0, 0, 0, 0.2);
  padding: 1.5rem;
  border-radius: 4px;
  margin-bottom: 1.2rem;
}

.buttons {
  justify-content: center;
}
</style>

    