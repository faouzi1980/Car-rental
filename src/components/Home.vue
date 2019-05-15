<template>
  <section class="home section">
    <div class="has-text-centered">
      <img alt class="mBottom20" src="../assets/cars.png">
      <p class="title mBottom20">Book Your Car Now</p>
    </div>
    <div class="columns">
      <div class="column">
        <div class="field">
          <div class="control">
            <input
              v-model="location"
              class="input is-medium"
              type="text"
              placeholder="Pick up from"
            >
          </div>
        </div>
      </div>
      <div class="column">
        <div class="field">
          <p class="control has-icons-left">
            <flat-pickr
              v-model="date"
              :config="config"
              class="input is-medium"
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
        <button
          type="submit"
          @click="submit"
          class="button is-medium is-fullwidth is-primary"
        >Search</button>
      </div>
    </div>
    <p
      v-if="error"
      class="has-text-danger has-text-centered errorMsg"
    >Enter Location &amp; date to proceed</p>
  </section>
</template>

<script>
import flatPickr from "vue-flatpickr-component";
import "flatpickr/dist/flatpickr.css";
export default {
  name: "Home",
  data() {
    return {
      error: false,
      location: "",
      date: "",
      config: {
        minDate: "today"
      }
    };
  },
  methods: {
    submit() {
      if (this.location == "" || this.date == "") {
        this.error = true;
      } else {
        this.error = false;
        this.$emit("nextComponent", this.date);
      }
    }
  },
  components: {
    flatPickr
  }
};
</script>

<style scoped>
</style>
