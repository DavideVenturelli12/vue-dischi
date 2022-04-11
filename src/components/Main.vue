<template>
  <main>
    <div class="card-container">
      <div class="card" v-for="(item, index) in getApi" :key="index">
        <img :src="item.poster" :alt="item.author" />
        <h3>{{ item.title }}</h3>
        <p>{{ item.author }}</p>
        <p>{{ item.year }}</p>
      </div>
    </div>
  </main>
</template>

<script>
/*
author: "Bon Jovi"
genre: "Rock"
poster: "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg"
title: "New Jersey"
year: "1988"
*/
import axios from "axios";

export default {
  name: "MainComponent",
  data() {
    return {
      getApi: Array,
    };
  },
  mounted() {
    this.loadData();
  },
  methods: {
    loadData() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((response) => {
          //console.log(response);
          if (response.status === 200) {
            this.getApi = response.data.response;
            console.log(this.getApi);
            //console.log(this.getApi[0]);
          }
        })
        //errore in caso ci siano problemi con i dati dell'API
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
main {
  height: 95vh;

  background-color: #1e2d3b;
  padding: 0 20%;
  .card-container {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    padding: 50px 0;
    .card {
      width: 150px;
      height: 300px;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      margin-top: 20px;
      background-color: hsl(210deg 21% 23%);
      img {
        width: 120px;
        margin-top: 20px;
      }
      h3 {
        color: white;
        margin: 15px 0;
      }
      p {
        color: hsl(60deg 3% 49%);
        margin: 5px 0;
      }
    }
  }
}
</style>