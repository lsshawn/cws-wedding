<template>
<div>
  <v-container class="px-0">
    <v-layout column text-xs-center>
      <v-flex xs12>
        <app-header></app-header>
      </v-flex>
      <v-flex xs6 class="mx-5 mainContent" v-if="!confirm">
        <div class="display-1 yourName">Your name please</div>
        <v-autocomplete
        persistent-hint
        v-model="person"
        :items="names"
        class="nameInput"
        >
          <v-slide-x-reverse-transition
            slot="append-outer"
            mode="out-in"
          >
          </v-slide-x-reverse-transition>
        </v-autocomplete>

        <v-btn
          @click="submit(person)"
          class="submitBtn"
          depressed large dark
        >
          I'm here
        </v-btn>
      </v-flex>
      <transition name="fade">
        <app-confirm class="mainContent" v-if="confirm" :name="person" :table="table"></app-confirm>
      </transition>
    </v-layout>
  </v-container>
</div>
</template>

<script>
import axios from 'axios'
import AppConfirm from '~/components/AppConfirm.vue'
import AppHeader from '~/components/AppHeader.vue'

const airtableConfigs = {
  headers: {
    'Authorization': 'Bearer ' + process.env.AIRTABLE_API_KEY,
    'Content-type': 'application/json'
  }
}

const base = 'appoFYBEHv1cQiC8b'
const url = `https://api.airtable.com/v0/${base}/Table%201`

export default {
  components: {
    appConfirm: AppConfirm,
    appHeader: AppHeader
  },
  data () {
    return {
      data: {},
      person: '',
      table: '',
      names: [],
      confirm: false
    }
  },
  computed: {
  },
  methods: {
    async submit (person) {
      if (person && person !== '') {
        let seat = this.data.filter(i => i.fields.Name === person)
        if (seat) {
          this.table = seat[0].fields['Table Number']
          let id = seat[0].id
          this.confirm = true

          try {
            let res = await axios.patch(
              `${url}/${id}`,
              {
                'fields': {
                  'Attended': true
                }
              },
              airtableConfigs)
            console.log(res)
          } catch (err) {
            console.log(err)
          }

          // this.$router.push('/confirm')
        }
      } else {
        alert('Please enter your name')
      }
    }
  },
  async beforeMount () {
    try {
      let _data = []

      let getData = async (offset) => {
        let nextUrl = offset === undefined ? url : url + `?offset=${offset}`
        // console.log(nextUrl)
        let res = await axios.get(nextUrl, airtableConfigs)
        if (res) {
          // console.log(res.data.records)
          _data = _data.concat(res.data.records)
        }

        if (res.data.offset) {
          await getData(res.data.offset)
        }
      }

      await getData()

      this.data = _data
      this.names = this.data.reduce((arr, item) => {
        if (item.fields.Name) {
          arr.push(item.fields.Name)
        }
        return arr
      }, [])
    } catch (err) {
      console.log(err)
    }
  }
}
</script>

<style scoped>
.submitBtn {
  background-color: #5f7872 !important;
}

.nameInput {
  font-size: 20px !important;
}

a.v-list__tile.v-list__tile--link {
  font-size: 20px !important;
}
.mainContent {
  margin-top: 30px;
}

.yourName {
  color: #444;
  line-height: 1.5em !important;
  font-size: 33px !important;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 1s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>

