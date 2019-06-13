# StackedProgressBar

Vue Stacked Progress Bar component for multiple staged progress.

## Getting Started

Vue Stacked Progress Bar is a Single File Component can be used to exhibit data list in progress line.
I also provide a handy ui to represent comparing paired data values.


### Installing

You can install from npm

```
npm i vue-stacked-progress-bar

```

### Usage

Register Vue component and provide prop data.

```
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

```


### Demo

Here is a JSfiddle demo you can test. 

## License

This project is licensed under the MIT License

