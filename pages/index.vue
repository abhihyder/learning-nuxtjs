<template>
  <div>
    <b-container class="bv-example-row">
      <b-row class="justify-content-md-center">
        <b-col cols="12" md="6">
          <b-form @submit.prevent="searchWeatherInfo">
            <b-input-group class="mt-3">
              <b-form-input
                v-model="location"
                placeholder="Search location"
              ></b-form-input>
              <b-input-group-append>
                <b-button variant="info" type="submit">Search</b-button>
              </b-input-group-append>
            </b-input-group>
          </b-form>
        </b-col>
      </b-row>
      <b-row class="justify-content-md-center mt-4">
        <b-col cols="12" md="6">
          <!--weather card-->
          <div class="card">
            <img
              class=""
              src="https://i.imgur.com/a9sHoeY.jpg"
              alt="Card image cap"
            />
            <div class="card-img-overlay" style="height: 110px">
              <h3 v-if="weatherInfo" class="card-title text-white m-b-0 dl">
                {{ weatherInfo.name }}
              </h3>
              <!-- <small class="card-text text-white font-light"
                >Sunday 15 march</small
              > -->
            </div>
            <div class="card-body weather-small">
              <div class="row">
                <div class="col-8 b-r align-self-center">
                  <div class="d-flex">
                    <div class="display-6 text-info">
                      <i class="mdi mdi-weather-pouring"></i>
                    </div>
                    <div class="m-l-20">
                      <h1
                        v-if="weatherInfo.weather"
                        class="font-light text-info m-b-0"
                      >
                        {{ temperature(weatherInfo.main.temp) }}<sup>0</sup>C
                      </h1>
                      <small v-if="weatherInfo.weather">{{
                        weatherInfo.weather[0].main
                      }}</small>
                    </div>
                  </div>
                </div>
                <div v-if="weatherInfo.weather" class="col-4 text-center">
                  <h1 class="font-light text-info m-b-0">
                    {{ temperature(weatherInfo.main.feels_like) }}<sup>0</sup>C
                  </h1>
                  <small>Feels Like</small>
                </div>
              </div>
            </div>
          </div>
          <!--weather card ends-->
        </b-col>
      </b-row>
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
  mounted() {
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
    temperature(temp) {
      return Math.round(temp - 273)
    },
  },
}
</script>
<style scoped>
body {
  background-color: #000000;
}

.padding {
  padding: 10rem !important;
  margin-left: 200px;
}

.card-no-border .card {
  border-color: #d7dfe3;
  border-radius: 4px;
  -webkit-box-shadow: 0px 5px 20px rgba(0, 0, 0, 0.05);
  box-shadow: 0px 5px 20px rgba(0, 0, 0, 0.05);
}

.card-img-overlay {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  padding: 1.25rem;
}

html body .dl {
  display: inline-block;
}

.text-white {
  color: #ffffff !important;
}

.font-light {
  font-weight: 300;
}

.card-text:last-child {
  margin-bottom: 0;
}

.card-body {
  -ms-flex: 1 1 auto;
  flex: 1 1 auto;
  padding: 1.25rem;
}

.b-r {
  border-right: 1px solid rgba(120, 130, 140, 0.13);
}

.text-info {
  color: #1e88e5 !important;
}

.display-6 {
  font-size: 36px;
}

.mdi {
  display: inline-block;
  font-family: 'weathericons';
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.m-l-20 {
  margin-left: 20px;
}

.m-b-0 {
  margin-bottom: 0px;
}

small {
  font-size: 80%;
  font-weight: 400;
}
</style>