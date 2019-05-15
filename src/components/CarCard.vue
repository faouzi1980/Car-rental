<template>
  <div>
    <div class="columns">
      <div class="column is-one-quarter has-text-centered">
        <img class="carImg" :src="data.photo" alt>
      </div>
      <div class="column">
        <div class="columns">
          <div class="column">
            <div class="marginBottom1">
              <p class="title">{{data.name}}</p>
              <p class="subtitle">
                <box-icon name="map" type="solid" color="#5a5a5a"></box-icon>
                &nbsp;{{data.location}}
              </p>
            </div>

            <div class="columns is-mobile has-text-centered icons">
              <div class="column is-narrow">
                <p>
                  <box-icon color="#c8c8c8" name="group" type="solid"></box-icon>
                </p>
                <p>Seats: {{data.seats}}</p>
              </div>
              <div class="column is-narrow">
                <p>
                  <box-icon color="#c8c8c8" name="cog" type="solid"></box-icon>
                </p>
                <p>Type: {{data.transmission}}</p>
              </div>
              <div class="column is-narrow">
                <p>
                  <box-icon color="#c8c8c8" name="gas-pump" type="solid"></box-icon>
                </p>
                <p>Fuel: {{data.fuel_Type}}</p>
              </div>
            </div>
          </div>

          <div class="column is-narrow has-text-centered pricesection">
            <p class="is-size-4">₹ {{data.price}}</p>
            <br>
            <button
              :disabled="!isCarAvailable"
              :class="[isCarAvailable ? 'is-success' : 'is-light']"
              class="button is-fullwidth is-medium"
            >Book Now</button>
            <span class="has-text-danger" v-if="!isCarAvailable">Not Available on {{dayChosen}}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    data: Object,
    day: String
  },
  data() {
    return {
      dayChosen: "",
      availability: this.data.availability
    };
  },
  methods: {
    carAvailable() {
      if (this.data.availability.includes(this.dayChosen)) {
        console.log("Available for ", this.data.name);
        return true;
      }
    },
    parseDate(val) {
      var dt = new Date(val).toString();
      console.log(dt);
      return dt.split(" ")[0];
    }
  },
  computed: {
    isCarAvailable() {
      if (this.availability.includes(this.dayChosen)) {
        return true;
      } else {
        return false;
      }
    }
  },
  watch: {
    day(val) {
      this.dayChosen = this.parseDate(this.day);
    }
  },
  mounted() {
    this.dayChosen = this.parseDate(this.day);
  }
};
</script>

<style scoped>
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

.arrow {
  width: 15px !important;
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

