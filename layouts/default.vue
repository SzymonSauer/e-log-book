<template>
  <div>
    <b-navbar toggleable="md" variant="light">
      <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
<!--      <b-navbar-brand to="/">Dziennik elektroniczny XYZ</b-navbar-brand>-->

      <b-collapse is-nav id="nav_collapse">
        <b-navbar-nav>
          <template v-if="$auth.$state.loggedIn">
            <b-nav-item to="/">Strona główna</b-nav-item>
            <b-nav-item to="/marks">Marks</b-nav-item>
            <b-nav-item to="/presences">Presences</b-nav-item>
            <b-nav-item to="/timetable">Timetable</b-nav-item>
<!--            <b-nav-item to="/test">Test</b-nav-item>-->
<!--            <b-nav-item to="/secure">Test Secure</b-nav-item>-->
          </template>
          <template v-else>
<!--            <b-nav-item to="/" exact>Home</b-nav-item>-->
<!--            <b-nav-item to="/public">Public</b-nav-item>-->
          </template>

        </b-navbar-nav>
        <b-navbar-nav class="ml-auto">
          <template v-if="$auth.$state.loggedIn">
            <b-nav-item-dropdown :text="$auth.user.name" right>
              <b-dropdown-item @click="$auth.logout()">Logout</b-dropdown-item>
            </b-nav-item-dropdown>
<!--            <b-img :src="picture" class="mt-1" rounded="circle" width="30px" height="30px" />-->
          </template>
          <template v-else>
            <b-dropdown-item to="/login">Login</b-dropdown-item>
          </template>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <b-container class="mt-4">
      <nuxt />
    </b-container>
  </div>
</template>

<script>
import dotProp from 'dotprop'

export default  {
  computed: {
    picture() {
      return  dotProp(this.$auth.user, 'picture') ||  // OpenID
              dotProp(this.$auth.user, 'picture.data.url') || // Facebook graph API
              dotProp(this.$auth.user, 'avatar_url') // GitHub
    }
  }

}
</script>
