<template>
  <div>
    <index-bar  :data="barData" @change="handlerChangeBar"/>
    <carousel/>
    <index-content :index-key="contentKey" @clickJournal="handlerClickJournal" :show-bar="isShowBar"/>
    <bottom/>
    <operator/>
  </div>
</template>

<script>
  import IndexBar from "./bar/index-bar";
  import Carousel from "./carousel/carousel";
  import Bottom from "./bottom/bottom";
  import Operator from "./operator/operator";
  import IndexContent from "./content/indexContent";
  export default {
    name: "index",
    components: {
      IndexContent,
      Operator,
      Bottom,
      Carousel, IndexBar},
    data() {
      return {
        isShowBar: true,
        contentKey: "/product",
        barData: [
          {
            showBar: false,
            key: "/home",
            title: "首页",
            children: [],
          },
          {
            key: "/product",
            title: "产品",
            children: [
              {
                title: "社区版"
              },
              {
                title: "企业版本"
              },
            ]
          },
          {
            title: "解决方案",
            children: [
              {
                title: "物联网解决方案111111111111"
              },
              {
                title: "物联网解决方案"
              },
            ]
          },
          {
            title: "服务与支持",
            children: [
              {
                title: "物联网解决方案111111111111"
              },
              {
                title: "物联网解决方案"
              },
            ]
          },
          {
            key: "/regardWe",
            title: "关于我们",
            children: [
              {
                title: "企业介绍"
              },
              {
                title: "荣誉资质"
              },
              {
                title: "新闻动态"
              },
              {
                title: "加入我们"
              },
              {
                title: "联系我们"
              },
            ]
          },
          {
            title: "文档",
            children: [],
          },
          {
            title: "LonglinDB社区",
            children: [],
          }
        ],
      }
    },
    methods: {
      handlerClickJournal(nows) {
        window.scrollTo(0, 0);
        this.contentKey = "/nows";
      },
      handlerChangeBar(data) {
        this.contentKey = data.parent.key;
        this.isShowBar = data.parent.showBar || true;
      }
    }
  }
</script>

<style scoped>

</style>
