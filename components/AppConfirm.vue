<template>
  <div>
    <div class="headline welcome pb-1">Thanks for coming,</div>
    <div class="name">{{ name }}</div>
    <v-flex xs12 class="pt-4">
    </v-flex>
    <v-flex xs12 class="tableNumber">
      <div class="tableTitle">TABLE</div>
      <div class="tableNo">{{ table }}</div>
    </v-flex>
  </div>
</template>

<script>
export default {
  props: ['name', 'table']
}
</script>

<style scoped>
.welcome {
  /* font-style: italic; */
  font-family: "Great Vibes";
  color: #777;
}

.tableTitle {
  letter-spacing: 5px;
  font-size: 1.5em;
  color: #666;
}

.name {
  font-size: 50px;
  color: #444;
}

.tableNo {
  font-family: "Great Vibes";
  font-size: 180px;
  color: #444;
  vertical-align: text-top;
  line-height: 80%;
}
</style>
