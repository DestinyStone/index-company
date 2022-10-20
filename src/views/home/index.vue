<template>
  <div style="min-width: 1200px;">
    <index-bar :data="barData" @change="handlerChangeBar"/>
    <carousel/>
    <index-content
        :nav-data="clickItems"
        :bar-data="titleBarData"
        :index-key="contentKey"
        @clickJournal="handlerClickJournal"
        :show-bar="isShowBar"/>
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
        oldParent: {},
        clickItems: [],
        titleBarData: [],
        isShowBar: false,
        contentKey: "/home",
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
                title: "数字孪生解决方案"
              },
              {
                title: "物联网解决方案"
              },
              {
                title: "数据智能解决方案"
              },
              {
                title: "实时交易解决方案"
              },
            ]
          },
          {
            title: "服务与支持",
            height: 300,
            left: 0,
            select: false,
            children: [
              {
                key: "/product/service",
                title: "物联网解决方案111111111111",
                slot: true,
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
            key: "/easy",
            title: "文档",
            children: [
              {
                title: "快速上手",
              },
              {
                title: "本地部署",
              },
              {
                title: "数据迁移",
              },
              {
                title: "备份恢复",
              },
              {
                title: "开发指南",
              }
            ],
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
        if (this.oldParent !== data.parent) {
          window.scrollTo(0, 0);
          this.oldParent = data.parent;
        }

        this.clickItems.splice(0, this.clickItems.length);
        this.clickItems.push(data.parent);
        if (data.children) {
          this.clickItems.push(data.children);
        }
        this.titleBarData = data.parent.children || [];


        this.contentKey = data.parent.key;

        let showBar = true;
        if (data.parent.showBar !== undefined && data.parent.showBar !== null) {
          showBar = data.parent.showBar;
        }
        this.isShowBar = showBar;
      },
      init() {
        document.getElementById("app").style.overflow = "unset";
      }
    },
    destroyed() {
      document.getElementById("app").style.overflow = "hidden";
    },
    mounted() {
      this.init();
    }
  }
</script>

<style scoped>

</style>
