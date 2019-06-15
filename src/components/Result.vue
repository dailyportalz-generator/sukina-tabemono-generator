<template>
  <div>
    <div class="messege">
      <p><img src="@/assets/fukidasshi_1_top.jpg"></p>
      <p class="name">こんにちは{{data.name}}です</p>
      <p><img src="@/assets/fukidasshi_2_bottom.jpg"></p>
    </div>
    <p><img :src="figureImg"></p>
    <p class="img" v-if="step >= 2"><img :src="foodImg"></p>
    <p class="img" v-if="step === 3"><img :src="charaImg"></p>
    <p class="share" v-if="step === 3">
      コピペ用 <input type="text" name="url" size="50" :value="shareUrl" readonly="readonly" class="edit" id="url" onfocus="this.select()">
    </p>
  </div>
</template>

<script>
import { stringify } from 'querystring'
export default {
  props: {
    data: Object,
    step: Number
  },
  data() {
    return {
    }
  },
  computed: {
    figureImg() {
      if(this.data.sex == 'female') {
        const images = [
          null,
          require('@/assets/mitame/female_1.jpg'),
          require('@/assets/mitame/female_2.jpg'),
          require('@/assets/mitame/female_3.jpg'),
          require('@/assets/mitame/female_4.jpg'),
          require('@/assets/mitame/female_5.jpg')
        ]
        return images[this.data.figure]
      } else {
        const images = [
          null,
          require('@/assets/mitame/male_1.jpg'),
          require('@/assets/mitame/male_2.jpg'),
          require('@/assets/mitame/male_3.jpg'),
          require('@/assets/mitame/male_4.jpg'),
          require('@/assets/mitame/male_5.jpg')
        ]
        return images[this.data.figure]
      }
    },
    foodImg() {
      if(this.data.sex == 'female') {
        if(this.data.figure == 1) {
          const images = [
            null,
            require('@/assets/tabemono/female_1_1.jpg'),
            require('@/assets/tabemono/female_1_2.jpg'),
            require('@/assets/tabemono/female_1_3.jpg'),
            require('@/assets/tabemono/female_1_4.jpg'),
            require('@/assets/tabemono/female_1_5.jpg')
          ]
          return images[this.data.food]
        } else if(this.data.figure == 2) {
          const images = [
            null,
            require('@/assets/tabemono/female_2_1.jpg'),
            require('@/assets/tabemono/female_2_2.jpg'),
            require('@/assets/tabemono/female_2_3.jpg'),
            require('@/assets/tabemono/female_2_4.jpg'),
            require('@/assets/tabemono/female_2_5.jpg')
          ]
          return images[this.data.food]
        } else if(this.data.figure == 3) {
          const images = [
            null,
            require('@/assets/tabemono/female_3_1.jpg'),
            require('@/assets/tabemono/female_3_2.jpg'),
            require('@/assets/tabemono/female_3_3.jpg'),
            require('@/assets/tabemono/female_3_4.jpg'),
            require('@/assets/tabemono/female_3_5.jpg')
          ]
          return images[this.data.food]
        } else if(this.data.figure == 4) {
          const images = [
            null,
            require('@/assets/tabemono/female_4_1.jpg'),
            require('@/assets/tabemono/female_4_2.jpg'),
            require('@/assets/tabemono/female_4_3.jpg'),
            require('@/assets/tabemono/female_4_4.jpg'),
            require('@/assets/tabemono/female_4_5.jpg')
          ]
          return images[this.data.food]
        } else if(this.data.figure == 5) {
          const images = [
            null,
            require('@/assets/tabemono/female_5_1.jpg'),
            require('@/assets/tabemono/female_5_2.jpg'),
            require('@/assets/tabemono/female_5_3.jpg'),
            require('@/assets/tabemono/female_5_4.jpg'),
            require('@/assets/tabemono/female_5_5.jpg')
          ]
          return images[this.data.food]
        }
      } else {
        if(this.data.figure == 1) {
          const images = [
            null,
            require('@/assets/tabemono/male_1_1.jpg'),
            require('@/assets/tabemono/male_1_2.jpg'),
            require('@/assets/tabemono/male_1_3.jpg'),
            require('@/assets/tabemono/male_1_4.jpg'),
            require('@/assets/tabemono/male_1_5.jpg')
          ]
          return images[this.data.food]
        } else if(this.data.figure == 2) {
          const images = [
            null,
            require('@/assets/tabemono/male_2_1.jpg'),
            require('@/assets/tabemono/male_2_2.jpg'),
            require('@/assets/tabemono/male_2_3.jpg'),
            require('@/assets/tabemono/male_2_4.jpg'),
            require('@/assets/tabemono/male_2_5.jpg')
          ]
          return images[this.data.food]
        } else if(this.data.figure == 3) {
          const images = [
            null,
            require('@/assets/tabemono/male_3_1.jpg'),
            require('@/assets/tabemono/male_3_2.jpg'),
            require('@/assets/tabemono/male_3_3.jpg'),
            require('@/assets/tabemono/male_3_4.jpg'),
            require('@/assets/tabemono/male_3_5.jpg')
          ]
          return images[this.data.food]
        } else if(this.data.figure == 4) {
          const images = [
            null,
            require('@/assets/tabemono/male_4_1.jpg'),
            require('@/assets/tabemono/male_4_2.jpg'),
            require('@/assets/tabemono/male_4_3.jpg'),
            require('@/assets/tabemono/male_4_4.jpg'),
            require('@/assets/tabemono/male_4_5.jpg')
          ]
          return images[this.data.food]
        } else if(this.data.figure == 5) {
          const images = [
            null,
            require('@/assets/tabemono/male_5_1.jpg'),
            require('@/assets/tabemono/male_5_2.jpg'),
            require('@/assets/tabemono/male_5_3.jpg'),
            require('@/assets/tabemono/male_5_4.jpg'),
            require('@/assets/tabemono/male_5_5.jpg')
          ]
          return images[this.data.food]
        }
      }
    },
    charaImg() {
      if(this.data.sex == 'female') {
        if(this.data.figure == 1) {
          const images = [
            null,
            require('@/assets/seikaku/female_1_1.jpg'),
            require('@/assets/seikaku/female_1_2.jpg'),
            require('@/assets/seikaku/female_1_3.jpg'),
            require('@/assets/seikaku/female_1_4.jpg'),
            require('@/assets/seikaku/female_1_5.jpg')
          ]
          return images[this.data.chara]
        } else if(this.data.figure == 2) {
          const images = [
            null,
            require('@/assets/seikaku/female_2_1.jpg'),
            require('@/assets/seikaku/female_2_2.jpg'),
            require('@/assets/seikaku/female_2_3.jpg'),
            require('@/assets/seikaku/female_2_4.jpg'),
            require('@/assets/seikaku/female_2_5.jpg')
          ]
          return images[this.data.chara]
        } else if(this.data.figure == 3) {
          const images = [
            null,
            require('@/assets/seikaku/female_3_1.jpg'),
            require('@/assets/seikaku/female_3_2.jpg'),
            require('@/assets/seikaku/female_3_3.jpg'),
            require('@/assets/seikaku/female_3_4.jpg'),
            require('@/assets/seikaku/female_3_5.jpg')
          ]
          return images[this.data.chara]
        } else if(this.data.figure == 4) {
          const images = [
            null,
            require('@/assets/seikaku/female_4_1.jpg'),
            require('@/assets/seikaku/female_4_2.jpg'),
            require('@/assets/seikaku/female_4_3.jpg'),
            require('@/assets/seikaku/female_4_4.jpg'),
            require('@/assets/seikaku/female_4_5.jpg')
          ]
          return images[this.data.chara]
        } else if(this.data.figure == 5) {
          const images = [
            null,
            require('@/assets/seikaku/female_5_1.jpg'),
            require('@/assets/seikaku/female_5_2.jpg'),
            require('@/assets/seikaku/female_5_3.jpg'),
            require('@/assets/seikaku/female_5_4.jpg'),
            require('@/assets/seikaku/female_5_5.jpg')
          ]
          return images[this.data.chara]
        }
      } else {
        if(this.data.figure == 1) {
          const images = [
            null,
            require('@/assets/seikaku/male_1_1.jpg'),
            require('@/assets/seikaku/male_1_2.jpg'),
            require('@/assets/seikaku/male_1_3.jpg'),
            require('@/assets/seikaku/male_1_4.jpg'),
            require('@/assets/seikaku/male_1_5.jpg')
          ]
          return images[this.data.chara]
        } else if(this.data.figure == 2) {
          const images = [
            null,
            require('@/assets/seikaku/male_2_1.jpg'),
            require('@/assets/seikaku/male_2_2.jpg'),
            require('@/assets/seikaku/male_2_3.jpg'),
            require('@/assets/seikaku/male_2_4.jpg'),
            require('@/assets/seikaku/male_2_5.jpg')
          ]
          return images[this.data.chara]
        } else if(this.data.figure == 3) {
          const images = [
            null,
            require('@/assets/seikaku/male_3_1.jpg'),
            require('@/assets/seikaku/male_3_2.jpg'),
            require('@/assets/seikaku/male_3_3.jpg'),
            require('@/assets/seikaku/male_3_4.jpg'),
            require('@/assets/seikaku/male_3_5.jpg')
          ]
          return images[this.data.chara]
        } else if(this.data.figure == 4) {
          const images = [
            null,
            require('@/assets/seikaku/male_4_1.jpg'),
            require('@/assets/seikaku/male_4_2.jpg'),
            require('@/assets/seikaku/male_4_3.jpg'),
            require('@/assets/seikaku/male_4_4.jpg'),
            require('@/assets/seikaku/male_4_5.jpg')
          ]
          return images[this.data.chara]
        } else if(this.data.figure == 5) {
          const images = [
            null,
            require('@/assets/seikaku/male_5_1.jpg'),
            require('@/assets/seikaku/male_5_2.jpg'),
            require('@/assets/seikaku/male_5_3.jpg'),
            require('@/assets/seikaku/male_5_4.jpg'),
            require('@/assets/seikaku/male_5_5.jpg')
          ]
          return images[this.data.chara]
        }
      }
    },
    shareUrl() {
      const shareData = {
        ...this.data,
        share: 1
      }
      return `https://dailyportalz.jp/p/generator/20190615tabemono?${stringify(
        shareData
      )}`
    }
  }
}
</script>

<style scope>
img {
  vertical-align: bottom;
}
div.messege {
  width: 320px;
}
p {
  margin: 0;
}
p.name {
  padding: 0 20px;
  background: url('../assets/fukidasshi_3_middle.jpg') repeat-y 0 0;
  font-size: 16px;
}
p.img {
  margin-top: 10px;
}
p.share {
  margin-top: 20px;
}
</style>
