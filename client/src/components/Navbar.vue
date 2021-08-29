<template>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container-fluid">
      <router-link class="navbar-brand" to="/">MEVN Auth</router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <router-link class="nav-link" to="/">Home</router-link>
        </li>
        <li class="nav-item">
            <router-link class="nav-link" to="/about">About</router-link>
        </li>
        <li class="nav-item">
            <router-link class="nav-link" to="/login" v-if="!isLoggedIn">Login</router-link>
        </li>
        <li class="nav-item">
            <router-link class="nav-link" to="/register" v-if="!isLoggedIn">Register</router-link>
        </li>
        <li class="nav-item">
            <router-link class="nav-link" to="/profile" v-if="isLoggedIn">Profile</router-link>
        </li>
        <li class="nav-item">
            <a class="nav-link" to="/logout" @click.prevent="logoutUser" v-if="isLoggedIn">Logout</a>
        </li>                         
      </ul>

    </div>
  </div>
</nav>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
    computed: {
        ...mapGetters(["isLoggedIn"])
    },
    methods: {
        ...mapActions(['logout']),
        logoutUser(){
            this.logout()
        }
    }
};
</script>

<style>

</style>
