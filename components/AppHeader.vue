<template>
  <v-flex xs12 class="mb-3">
    <div class="display-2 brideGroom" id="ws">Wei Siong</div>
    <div class="display-1 brideGroom" id="ampersand">&</div>
    <div class="display-2 brideGroom" id="valerie">Valerie</div>
    <!-- <hr class="separator"> -->
    <div class="date">29 Sept 2018</div>
  </v-flex>
</template>

<style scoped>

.brideGroom {
  font-family: 'Great Vibes' !important;
  /* position: absolute; */
  font-size: 80px;
  width: 100%;
}

#ws {
  z-index: 1;
  /* padding-right: 80px; */
}

#ampersand {
  font-family: 'Great Vibes' !important;
  color: #777;
  /* margin:40px 0 0; */
  z-index:2;
  font-size: 25px !important;
  opacity: 0.5 !important;
}

#valerie {
  /* margin: 70px 0 0 0;  */
  z-index: 3;
}

.separator {
  width: 80%;
  margin: 10px auto;
  border-radius: 1px;
  border: 0;
  height: 1px;
  /* margin: 10px 0 10px 0; */
  background: #999;
  margin-bottom: 0;
}

.date {
  color: #888;
  font-style: italic;
  text-transform: uppercase;
}
</style>
