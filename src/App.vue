<script>
import axios from "axios"
import CardList from './components/CardList.vue';
import AppSearch from './components/AppSearch.vue';
import TotalResult from './components/TotalResult.vue';
import { store } from "./store";

export default {
  components: { 
    CardList,
    AppSearch,
    TotalResult,
  },
  data() {
    return {
      store,
    };
  },
  created() {
    axios.get("https://rickandmortyapi.com/api/character").then((resp) => {
      console.log(resp)
      this.store.characterArray = resp.data.results;
    });
  },
  methods: {
    showChar(){
      console.log(this.store.selectedStatus);

      const paramsObj = {
        status: ""
      }

      if(this.store.selectedStatus !== "All") {
        paramsObj.status = this.store.selectedStatus;
      }

      axios.get("https://rickandmortyapi.com/api/character", {
        params: paramsObj
      }).then((resp) => {
      console.log(resp)
      this.store.characterArray = resp.data.results;
    });

    }
  }
};
</script>
 
<template>
  <h1>Rick and Morty App</h1>
  <AppSearch @statusChanged="showChar"/>
  <CardList/>
  <TotalResult/>
</template>

<style scoped>
h1 {
  padding: 50px 0;
  text-align: center;
}
</style>
