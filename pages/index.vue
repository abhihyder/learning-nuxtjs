<template>
  <div>
    <b-container class="bv-example-row mt-4">
      <div class="d-flex justify-content-center mt-3">
        <div style="max-width: 20rem" class="mb-2">
          <b-input-group class="mt-3">
            <b-form-input
              v-model="location"
              placeholder="Search location"
            ></b-form-input>
            <b-input-group-append>
              <b-button variant="info" @click="searchWeatherInfo"
                >Search</b-button
              >
            </b-input-group-append>
          </b-input-group>
        </div>
      </div>
      <div class="d-flex justify-content-center mt-3">
        <b-card
          title="Card Title"
          img-src="https://picsum.photos/600/300/?image=25"
          img-alt="Image"
          img-top
          tag="article"
          style="max-width: 20rem"
          class="mb-2"
        >
          <b-card-text>
            Some quick example text to build on the card title and make up the
            bulk of the card's content.
          </b-card-text>

          <b-button href="#" variant="primary">Go somewhere</b-button>
        </b-card>
      </div>
    </b-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      location: 'Dhaka',
      weatherInfo: {},
    }
  },
  created() {
    this.searchWeatherInfo()
  },
  methods: {
    searchWeatherInfo() {
      this.$axios
        .$get(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.location}&appid=${process.env.weatherApiKey}`
        )
        .then((response) => {
          this.weatherInfo = response
        })
    },
  },
}
</script>
