
<template>
  <section class="section">
    <div class="container">
      <h1 class="title">
        Hello World
      </h1>
      <p class="has-text-primary">
        My first website with <strong>Bulma</strong>!
      </p>
      <p>
        <a class="button is-primary">Primary</a>
        <a class="button is-link">Link</a>
        <a class="button is-info">Info</a>
        <a class="button is-success">Success</a>
        <a class="button is-warning">Warning</a>
        <a class="button is-danger">Danger</a>
        </p>
   </div>
    <div class="container">
    <canvas id="planet-chart"></canvas>
    </div>
  </section>
</template>

<script>
/* eslint-disable */
import Chart from 'chart.js';
import planetChartData from '../chart-data.js'

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      planetChartData: planetChartData,
    }
  },
  methods: {
    createChart(chartId, chartData) {
      const ctx = document.getElementById(chartId);
      const myChart = new Chart(ctx, {
        type: chartData.type,
        data: chartData.data,
        options: chartData.options,
      })
    }
  },
  mounted() {
    this.createChart('planet-chart', this.planetChartData)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" >
</style>
