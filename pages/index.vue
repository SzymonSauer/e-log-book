<template>
  <div>
    <template v-if="$auth.$state.loggedIn">

      <div class="mt-1">
        <h4>Brak wiadomości.</h4>
      </div>
    </template>
    <template v-else>
      <b-jumbotron class="text-center">
        <h3>Dziennik elektroniczny</h3>
        Szkoła XYZ
        <div class="mt-1">
          <b-btn variant="success" to="/login">Login</b-btn>
        </div>
      </b-jumbotron>


    </template>

<!--    <div>-->
<!--      User status:-->
<!--      <b-badge>{{ $auth.$state.loggedIn ? 'Logged In' : 'Guest' }}</b-badge>-->
<!--    </div>-->
  </div>
</template>

<!--<script>-->
<!-- import { version } from '../package.json'-->

<!--export default {-->
<!--  computed: {-->
<!--    version: () => version-->
<!--  }-->
<!--}-->
<!--</script>-->
