<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-container class="bv-example-row">
        <b-navbar-brand href="javascript:;">Weather App</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <n-link class="nav-link" active-class="active" exact to="/"
                >Home</n-link
              >
            </li>
            <li class="nav-item">
              <n-link class="nav-link" active-class="active" exact to="/about"
                >About</n-link
              >
            </li>
          </ul>

          <!-- Right aligned nav items -->
          
        </b-collapse>
      </b-container>
    </b-navbar>
    <Nuxt />
  </div>
</template>

<script>
export default {}
</script>
