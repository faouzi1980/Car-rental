<template>
  <section>
    <div v-if="loading" class="loading">
      <box-icon name="loader-alt" size="lg" animation="spin" color="#c8c8c8"></box-icon>
    </div>
    <ul v-else>
      <li v-for="(car, index) in cars" :key="index">
        <div>
          <div class="columns">
            <div class="column is-one-quarter has-text-centered">
              <img class="carImg" :src="car.photo" alt>
            </div>
            <div class="column">
              <div class="columns">
                <div class="column">
                  <div class="marginBottom1">
                    <p class="title">{{car.name}}</p>
                    <p class="subtitle">
                      <box-icon name="map" type="solid" color="#5a5a5a"></box-icon>
                      &nbsp;{{car.location}}
                    </p>
                  </div>

                  <div class="columns is-mobile has-text-centered icons">
                    <div class="column is-narrow">
                      <p>
                        <box-icon color="#c8c8c8" name="group" type="solid"></box-icon>
                      </p>
                      <p>Seats: {{car.seats}}</p>
                    </div>
                    <div class="column is-narrow">
                      <p>
                        <box-icon color="#c8c8c8" name="cog" type="solid"></box-icon>
                      </p>
                      <p>Type: {{car.transmission}}</p>
                    </div>
                    <div class="column is-narrow">
                      <p>
                        <box-icon color="#c8c8c8" name="gas-pump" type="solid"></box-icon>
                      </p>
                      <p>Fuel: {{car.fuel_Type}}</p>
                    </div>
                  </div>
                </div>

                <div class="column is-narrow has-text-centered pricesection">
                  <p class="is-size-4">₹ {{car.price}}</p>
                  <br>
                  <button class="button is-fullwidth is-medium is-success">Book Now</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </li>
    </ul>
  </section>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      loading: false,
      cars: [],
      apiUrl: "https://api.sheety.co/311576ae-321a-43e3-9a5b-61b3ac373d85",
      page: 1,
      perPage: 6,
      pages: []
    };
  },
  mounted() {
    this.loading = true;
    axios
      .get(this.apiUrl)
      .then(response => {
        console.log("Done");
        response.data.forEach(item => {
          this.cars.push(item);
        });
        this.loading = false;
      })
      .catch(error => {
        this.loading = true;
      });
  }
};
</script>


<style scoped>
.loading {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.subtitle {
  display: flex;
}

.icons {
  flex-wrap: wrap;
}

.pricesection {
  flex-direction: column;
  display: flex;
  justify-content: center;
}

.marginBottom1 {
  margin-bottom: 16px;
}
.carImg {
  width: 200px;
}

li {
  box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.14),
    0 3px 1px -2px rgba(0, 0, 0, 0.12), 0 1px 5px 0 rgba(0, 0, 0, 0.2);
  padding: 1.5rem;
  border-radius: 4px;
}

li:not(:last-child) {
  margin-bottom: 1.2rem;
}

@media (min-width: 320px) and (max-width: 480px) {
  .icons {
    justify-content: space-around;
  }

  .title {
    text-align: center;
  }

  .subtitle {
    justify-content: center;
  }
}
</style>

    