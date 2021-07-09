<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-container class="bv-example-row">
        <b-navbar-brand href="javascript:;">Weather App</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item href="#"> hello</b-nav-item>
            <b-nav-item href="#"> hey</b-nav-item>
          </b-navbar-nav>

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto mr-2">
            <b-nav-form>
              <b-form-input
                size="sm"
                class="mr-sm-2"
                placeholder="Search location"
              ></b-form-input>
              <b-button size="sm" class="my-2 my-sm-0" type="submit"
                >Search</b-button
              >
            </b-nav-form>
          </b-navbar-nav>
        </b-collapse>
      </b-container>
    </b-navbar>
    <Nuxt />
  </div>
</template>

<script>
export default {}
</script>
