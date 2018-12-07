
<template>
  <section class="section">
    <div class="container">
      <h1 class="title">
       FabCar
      </h1>
      <p>
        <a class="button is-primary" v-on:click="getallcars">Get All Cars</a>
        </p>
   </div>
    <div class="container">
      <table class="table">
      <thead>
          <tr>
            <th>Key</th>
            <th>Color</th>
            <th>Make</th>
            <th>Model</th>
            <th>Owner</th>
            <th>Action</th>
          </tr>
      </thead>
      <tbody>
        <tr v-for="car of cars" v-bind:key="car.key">
          <td>{{car.Key}}</td>
          <td>{{car.Record.color}}</td>
          <td>{{car.Record.make}}</td>
          <td>{{car.Record.model}}</td>
          <td>{{car.Record.owner}}</td>
          <td><div class="field has-addons">
  <div class="control">
    <input class="input" type="text" placeholder="Find a repository">
  </div>
  <div class="control">
    <a class="button is-info">
      Search
    </a>
  </div>
</div></td>
        </tr>
      </tbody>
  </table>
    </div>
  </section>
</template>

<script>
/* eslint-disable */
import axios from 'axios';

export default {
  name: 'FabCar',
  data () {
    return {
      cars : []
    }
  },
  methods: {
    async getallcars(){
      console.log('Getting All Cars');
     try {
      const response = await axios.post(`http://localhost:3000/fabcar/queryAllCars`)
      console.log(response.data);
      JSON.parse(response.data).forEach((e)=>{
        this.cars.push(e)
      })
    } catch (e) {
     console.log(e);
    }
    },
    async changeowner(key){
      console.log(`Changing owner of ${key}`)
    }
  },
  mounted() {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" >
</style>
