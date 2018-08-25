<template>
  <v-app>
    <v-content class="fullContainer">
      <nuxt/>
    </v-content>
  </v-app>
</template>

<script>
</script>

<style>
.application--wrap {
  background-color: #fff;
}

.fullContainer {
  height: 100%;
  background: url('~/assets/images/table-number.png') no-repeat center center fixed;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  /* margin-bottom: 40px; */
}
</style>
