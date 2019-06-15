<template>
  <form @submit.prevent="handleSubmit">
    <p>なまえ <input type="text" v-model="name"></p>
    <p><label for="male"><input type="radio" name="sex" value="male" id="male" v-model="sex">男</label><br>
    <label for="female"><input type="radio" name="sex" value="female" id="female" v-model="sex">女</label></p>
    <dl>
      <dt>見た目のタイプ</dt>
      <dd><label for="figure1"><input type="radio" name="figure" id="figure1" value="1" v-model="figure"> 普通ですよ</label></dd>
      <dd><label for="figure2"><input type="radio" name="figure" id="figure2" value="2" v-model="figure"> メガネですね</label></dd>
      <dd><label for="figure3"><input type="radio" name="figure" id="figure3" value="3" v-model="figure"> 老けてるって言われるのう</label></dd>
      <dd><label for="figure4"><input type="radio" name="figure" id="figure4" value="4" v-model="figure"> けっこう宇宙的</label></dd>
      <dd><label for="figure5"><input type="radio" name="figure" id="figure5" value="5" v-model="figure"> メカニカルだ</label></dd>
    </dl>
    <button>つぎへ</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
        name: '',
        sex: 'male',
        figure: 1
    }
  },
  methods: {
    handleSubmit() {
      this.$emit('basic', {
        name: this.name,
        sex: this.sex,
        figure: this.figure
      })
    }
  }
}
</script>

<style scoped>
p:first-child {
  margin-bottom: 10px;
}
dl dt {
  margin-bottom: 10px;
  color: #f60;
  font-weight: bold;
}
dl dd {
  margin: 0;
}
</style>
