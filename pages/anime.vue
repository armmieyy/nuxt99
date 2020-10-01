<template>
  <div class="row text-light">
    <div class="col-sm" />

    <div class="col-sm">
      <input v-model="textSearch" type="text" placeholder="ค้นหาการ์ตูน">
      <v-btn
        squared
        variant="outline-danger"
        @click="searchData()"
      >
        Search
      </v-btn>
      <li
        v-for="data in animeData"
        :key="data.mal_id"
      >
        <nuxt-link :to="{ name: 'product-id', params: { data: data } }">
          {{ data.title }}
        </nuxt-link>
      </li>
      <br>
      <br>
    </div>

    <div class="col-sm" />
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      animeData: null,
      textSearch: '',
      perPage: 9,
      currentPage: 1,
      run: false
    }
  },
  methods: {
    searchData () {
      axios
        .get('https://api.jikan.moe/v3/search/anime?q=' + this.textSearch + '')
        .then((response) => {
          this.animeData = response.data.results.slice(0, 100)
        })
        .catch((err) => {
          // eslint-disable-next-line no-console
          console.log(err)
        })
    }
  }
}
</script>

<style>
.card {
  background-color: rgb(45, 110, 175);
}
.pagination {
  justify-content: center;
}
</style>
