<template>
  <div id="app">
    <template v-if="isError"><img src="@/assets/error.jpg"></template>
    <template v-else>
      <Result
        :step="step"
        :data="data"
        v-if="step >= 1" />
      <InputBasic
        key="basic"
        v-if="step === 0"
        @basic="handleBasic" />
      <InputFood
        key="food"
        v-if="step === 1"
        @food="handleFood"/>
      <InputChara
        key="chara"
        v-if="step === 2"
        @chara="handleChara" />
    </template>
  </div>
</template>

<script>
import { parse } from 'querystring'
import Result from './components/Result.vue'
import InputBasic from './components/InputBasic.vue'
import InputFood from './components/InputFood.vue'
import InputChara from './components/InputChara.vue'

export default {
  name: 'app',
  data() {
    return {
      step: 0,
      data: {
        name: '',
        sex: 1,
        figure: 1,
        food: 1,
        chara: 1,
      }
    }
  },
  mounted() {
    const params = parse(location.search.replace('?', ''))
    const isValid = ['name', 'sex', 'figure', 'food', 'chara'].every((val) => {
      if (!params[val]) {
        return false
      }
      if (val != 'name' && parseInt(params[val]) < 1) {
        return false
      }
      return true
    })
    if (isValid) {
      const data = {
        name: params.name,
        title: parseInt(params.title),
        q1: parseInt(params.q1),
        sex: parseInt(params.sex),
        figure: parseInt(params.figure),
        food: parseInt(params.food),
        chara: parseInt(params.chara)
      }
      this.data = data
      this.step = 3
    }
  },
  methods: {
    handleNext() {
      this.step ++
    },
    handleBasic(basic) {
      this.data.name = basic.name
      this.data.sex = basic.sex
      this.data.figure = basic.figure

      this.handleNext()
    },
    handleFood(food) {
      this.data.food = food.food
      this.handleNext()
    },
    handleChara(chara) {
      this.data.chara = chara.chara
      this.handleNext()
    }
  },
  components: {
    Result,
    InputBasic,
    InputFood,
    InputChara
  },
  computed: {
    isError(){
      if( this.step === 1 && this.data.name == '' ) {
        console.log('error1')
        return true
      } else if ( this.step === 2 && this.data.food == '' ) {
        console.log(this.data.food)
        return true
      } else if ( this.step === 3 && this.data.chara == '' ) {
        console.log('error3')
        return true
      } else {
        return false
      }
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

#app {
  font-family: sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  max-width: 640px;
  font-size: 14px;
  padding: 0 50px;
}
</style>
