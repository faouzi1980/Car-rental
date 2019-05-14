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
            <button class="button is-fullwidth is-medium is-success">Book Now</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    data: Object
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

