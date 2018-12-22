<template>
  <div class="home">
    <div :class="'avatar-box-'+imagesListLength">
      <img class="img" :src="value" v-for="(value,index) in list" :key="index">
    </div>
    <button v-for="(value,index) in 9" :key="index" @click="handelButton(value)">{{value}}</button>
  </div>
</template>

<script>
// 导入图片列表
const images = require.context(
  "@/assets/images/",
  true,
  /\.(png|jpe?g|gif|svg)(\?.*)?$/
);
let imagesList = [];
images.keys().forEach(filePath => {
  imagesList.push(images(filePath));
});

export default {
  // 计算图片列表长度
  computed: {
    list: function() {
      return this.imagesList.slice(0, this.imagesListLength);
    }
  },
  data() {
    return {
      // 图片列表
      imagesList,
      // 图片列表长度
      imagesListLength: 1
    };
  },
  methods: {
    // 点击button切换图片数量
    handelButton(val) {
      this.imagesListLength = val;
    }
  }
};
</script>

<style lang="less" scoped>
@import "../assets/less/index";
button {
  margin-top: 20px;
  width: 50px;
  height: 50px;
}
</style>

