<template>
  <div>
    <div class="headline welcome pb-1">Thanks for coming,</div>
    <div class="display-1 name">{{ name }}</div>
    <v-flex xs12 class="pt-4">
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
  color: #999;
}

.tableTitle {
  letter-spacing: 5px;
  font-size: 1.5em;
  color: #666;
}

.tableNo {
  font-family: "Great Vibes";
  font-size: 8em;
  color: #666;
  vertical-align: text-top;
}
</style>
