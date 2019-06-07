<template>
  <div id="app">
    <StackedProgressBar :list="values" :striped="false" :label-location="labelLocation"/>
  </div>
</template>

<script>

import StackedProgressBar from './components/StackedProgressBar.vue'

export default {
  name: 'app',
  components: {
    StackedProgressBar
  },
  data() {
    return {
      values: [
        { text: '20.TL', description: 'İlk Taksit', percentage: 30, striped: true, color: '#60c558'},
        { text: '1220.TL', description: 'Toplam Ödeme', percentage: 30, striped: false, color: '#60c558' }
        // { text: '420.TL', description: 'Kalan', percentage: 60, striped: true, color: '#edabba' }
        ],
      labelLocation: 'outside'

    }
  }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
