<template>
  <nav class="navbar is-light" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a class="navbar-item" href="https://bulma.io">
        <span class="subtitle">CAR Rentals</span>
      </a>

      <a
        role="button"
        class="navbar-burger burger"
        aria-label="menu"
        aria-expanded="false"
        data-target="navbarBasicExample"
        @click="isActive = !isActive"
        :class="{'is-active' : isActive}"
      >
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>

    <div id="navbarBasicExample" class="navbar-menu" :class="{'is-active' : isActive}">
      <div class="navbar-start">
        <div class="navbar-item has-dropdown is-hoverable">
          <a class="navbar-link">Sort</a>
          <div class="navbar-dropdown">
            <a class="navbar-item" @click="sort('low')">Low to high</a>
            <a class="navbar-item" @click="sort('high')">High to low</a>
          </div>
        </div>

        <div class="navbar-item has-dropdown is-hoverable">
          <a class="navbar-link">Car type</a>
          <div class="navbar-dropdown">
            <a class="navbar-item" @click="filterCar('All')">All</a>
            <a class="navbar-item" @click="filterCar('Hatchback')">Hatchback</a>
            <a class="navbar-item" @click="filterCar('Sedan')">Sedan</a>
            <a class="navbar-item" @click="filterCar('SUV')">SUV</a>
            <a class="navbar-item" @click="filterCar('Mini SUV')">Mini SUV</a>
          </div>
        </div>

        <div class="navbar-item has-dropdown is-hoverable">
          <a class="navbar-link">Transmission</a>
          <div class="navbar-dropdown">
            <a class="navbar-item" @click="transmissionFilter('All')">All</a>
            <a class="navbar-item" @click="transmissionFilter('Automatic')">Automatic</a>
            <a class="navbar-item" @click="transmissionFilter('Manual')">Manual</a>
          </div>
        </div>

        <div class="navbar-item has-dropdown is-hoverable">
          <a class="navbar-link">Fuel</a>
          <div class="navbar-dropdown">
            <a class="navbar-item" @click="fuelFilter('All')">All</a>
            <a class="navbar-item" @click="fuelFilter('Petrol')">Petrol</a>
            <a class="navbar-item" @click="fuelFilter('Diesel')">Diesel</a>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>
<script>
export default {
  name: "Navbar",
  data() {
    return {
      isActive: false
    };
  },
  methods: {
    filterCar(val) {
      this.isActive = false;
      this.$emit("carTypeFilter", val);
    },
    sort(val) {
      this.isActive = false;
      this.$emit("sort", val);
    },
    transmissionFilter(val) {
      this.isActive = false;
      this.$emit("transmissionFilter", val);
    },
    fuelFilter(val) {
      this.isActive = false;
      this.$emit("fuelFilter", val);
    }
  }
};
</script>
