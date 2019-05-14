<template>
  <section>
    <ul>
      <li>
        <div>
          <div class="columns">
            <div class="column is-one-quarter has-text-centered">
              <img
                class="carImg"
                src="https://jtride-data.s3.ap-south-1.amazonaws.com/uploads/1517236166_1509779915_152_i10.webp"
                alt
              >
            </div>
            <div class="column">
              <div class="columns">
                <div class="column">
                  <div class="marginBottom1">
                    <p class="title">Hyundai Grand i10</p>
                    <p class="subtitle">
                      <box-icon name="map" type="solid" color="#5a5a5a"></box-icon>&nbsp;Koramangala
                    </p>
                  </div>

                  <div class="columns is-mobile has-text-centered icons">
                    <div class="column is-narrow">
                      <p>
                        <box-icon color="#c8c8c8" name="group" type="solid"></box-icon>
                      </p>
                      <p>Seats: 5</p>
                    </div>
                    <div class="column is-narrow">
                      <p>
                        <box-icon color="#c8c8c8" name="cog" type="solid"></box-icon>
                      </p>
                      <p>Transmission: Manual</p>
                    </div>
                    <div class="column is-narrow">
                      <p>
                        <box-icon color="#c8c8c8" name="gas-pump" type="solid"></box-icon>
                      </p>
                      <p>Fuel: Diesel</p>
                    </div>
                  </div>
                </div>

                <div class="column is-narrow has-text-centered pricesection">
                  <p class="is-size-4">₹ 4000</p>
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

li {
  box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.14),
    0 3px 1px -2px rgba(0, 0, 0, 0.12), 0 1px 5px 0 rgba(0, 0, 0, 0.2);
  padding: 1.5rem;
  border-radius: 4px;
}

li:not(:last-child) {
  margin-bottom: 1.2rem;
}
</style>

    