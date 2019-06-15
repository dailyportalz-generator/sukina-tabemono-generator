<template>
  <form @submit.prevent="handleSubmit">
    <dl>
      <dt>一番近い性格を選んでください</dt>
      <dd><label for="chara1"><input type="radio" name="chara" id="chara1" value="1" v-model="chara"> 明るいよ</label></dd>
      <dd><label for="chara2"><input type="radio" name="chara" id="chara2" value="2" v-model="chara"> 暗いです</label></dd>
      <dd><label for="chara3"><input type="radio" name="chara" id="chara3" value="3" v-model="chara"> おっとりしてます</label></dd>
      <dd><label for="chara4"><input type="radio" name="chara" id="chara4" value="4" v-model="chara"> せっかちだ</label></dd>
      <dd><label for="chara5"><input type="radio" name="chara" id="chara5" value="5" v-model="chara"> いい人ですよ</label></dd>
      <dd><label for="chara6"><input type="radio" name="chara" id="chara6" value="6" v-model="chara"> 悪人に決まってるだろう</label></dd>
    </dl>
    <button>つぎへ</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      chara: 1
    }
  },
  methods: {
    handleSubmit() {
      this.$emit('chara', {
        chara: this.chara
      })
    }
  }
}
</script>

<style>
</style>
