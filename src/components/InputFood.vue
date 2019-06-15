<template>
  <form @submit.prevent="handleSubmit">
    <dl>
      <dt>好きな食べものは</dt>
      <dd><label for="food1"><input type="radio" name="food" id="food1" value="1" v-model="food"> 肉</label></dd>
      <dd><label for="food2"><input type="radio" name="food" id="food2" value="2" v-model="food"> 魚</label></dd>
      <dd><label for="food3"><input type="radio" name="food" id="food3" value="3" v-model="food"> 野菜</label></dd>
      <dd><label for="food4"><input type="radio" name="food" id="food4" value="4" v-model="food"> 甘い物</label></dd>
      <dd><label for="food5"><input type="radio" name="food" id="food5" value="5" v-model="food"> ガソリン</label></dd>
    </dl>
    <button>つぎへ</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      food: 1
    }
  },
  methods: {
    handleSubmit() {
      this.$emit('food', {
        food: this.food
      })
    }
  }
}
</script>

<style scoped>
dl dt {
  margin-bottom: 10px;
  color: #f60;
  font-weight: bold;
}
dl dd {
  margin: 0;
}
</style>
