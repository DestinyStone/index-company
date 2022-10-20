<template>
  <index-item-container @mouseOutContent="handlerMouseOut"  class="product-center" background="#ffffff" min-title="产品中心" title="星微联关系数据库">
    <div slot="content">
      <el-row>
        <el-col :span="8" style="padding: 10px 15px;" >
          <div style="position:relative;" @mouseenter="activeIndex = oneData.id">
            <div class="item" style="border: 1px solid #F2F6FC; border-radius: 10px; padding: 20px;" >
              <div style="font-size: 26px; font-weight: 700" :style="{color: activeIndex === oneData.id ? '#ffffff' : '#2468F2'}">{{oneData.title}}</div>
              <div :class="{'item-content-active': activeIndex === oneData.id}"  class="item-content" style="line-height: 28px;" :style="{height: oneHeight === 0 ? 'unset' : oneHeight + 'px'}">
                <div v-for="(content, index) in oneData.content.split('\n')" :key="'content' + index">{{content}}</div>
              </div>
              <div style="display: flex; justify-content: start;">
                <el-button type="primary" v-if="activeIndex !== oneData.id">{{oneData.buttonText}}</el-button>
                <el-button type="primary" style="background: #ffffff; border: #ffffff; color: #409EFF;" v-else>{{oneData.buttonText}}</el-button>
              </div>
            </div>
            <div class="item-background-one" :class="{'active-item-background': activeIndex === oneData.id}">
            </div>
          </div>
        </el-col>
        <el-col :span="16">
          <el-row v-for="(item, index) in userData" :key="'item' + index">
            <el-col :span="12" v-for="(childrenItem, childrenIndex) in item" :key="'children' + childrenIndex" style="padding: 10px 15px;">
              <div style="position:relative;" @mouseenter="activeIndex = childrenItem.id">
                <div class="item" style="border: 1px solid #F2F6FC; border-radius: 10px; padding: 20px;">
                  <div style="font-size: 26px; font-weight: 700" :style="{color: activeIndex === childrenItem.id ? '#ffffff' : '#2468F2'}">{{childrenItem.title}}</div>
                  <div :class="{'item-content-active': activeIndex === childrenItem.id}" class="item-content" ref="itemContent" :style="{height: contentHeight === 0 ? 'unset' : contentHeight + 'px'}">
                    <div v-for="(content, index) in childrenItem.content.split('\n')"  :key="'content' + index">{{content}}</div>
                  </div>
                  <div style="display: flex; justify-content: end;">
                    <el-button size="small" type="primary" v-if="activeIndex !== childrenItem.id">{{childrenItem.buttonText}}</el-button>
                    <el-button size="small" type="primary" style="background: #ffffff; border: #ffffff; color: #409EFF;" v-else>{{childrenItem.buttonText}}</el-button>
                  </div>
                </div>
                <div class="item-background" :class="{'active-item-background': activeIndex === childrenItem.id}">
                </div>
              </div>
            </el-col>
          </el-row>
        </el-col>
      </el-row>
    </div>
  </index-item-container>
</template>

<script>
  import IndexItemContainer from "./index-item-container";
  export default {
    name: "index-item-product-center",
    components: {IndexItemContainer},
    data() {
      return {
        oneHeight: 0,
        contentHeight: 0,
        activeIndex: "1",
        data: [
          {
            id: "1",
            title: "社区版",
            content: "产品快速迭代，优先体验产品特性;\n开放 & 开源生态， 上下游社区项目丰富;\n广泛的社区用户 & 开发者支持;",
            buttonText: "免费下载",
          },
          {
            id: "2",
            title: "企业版",
            content: "15用户授权， 50并发授权",
            buttonText: "查看详情",
          },
          {
            id: "3",
            title: "数字孪生物联版",
            content: "50用户授权， 不限并发授权",
            buttonText: "查看详情",
          },
          {
            id: "4",
            title: "集团版",
            content: "不限制用户授权， 200并发授权",
            buttonText: "查看详情",
          },
          {
            id: "5",
            title: "定制版",
            content: "特定业务函数定制， 特定数据表模型定制",
            buttonText: "查看详情",
          }
        ]
      }
    },
    computed: {
      oneData() {
        return this.data[0];
      },
      userData() {
        if (this.data.length === 5) {
          return [[this.data[1], this.data[2]], [this.data[3], this.data[4]]];
        }
        return [];
      },
    },
    methods: {
      init() {
        this.setContentHeight();
      },
      setContentHeight() {
        setTimeout(() => {
          let height = 0;
          for(let item of this.$refs['itemContent']) {
            height = item.offsetHeight > height ? item.offsetHeight : height;
          }
          this.contentHeight = height;
          this.oneHeight = (this.contentHeight + 69) * 2;
        }, 30);
      },
      handlerMouseOut() {
        // this.activeIndex = "1";
      }
    },
    mounted() {
      this.init();
    }
  }
</script>

<style scoped>
  .product-center .item {
    position:relative;
    z-index: 999;
  }
  .product-center .item-content{
    font-size: 18px;
    color: #101010;
    margin-top: 15px;
  }
  .product-center .item-content-active {
    color: #ffffff !important;
  }
  .product-center .item-background-one {
    width: 100%;
    height: 100%;
    position: absolute;
    border-radius: 10px;
    top: 0;
    background: linear-gradient(rgba(102,204,255,0.7), rgba(102,204,255, 0.7)), url('/home/v2_rjdkha.png') no-repeat;
    background-position: 30% 80%;
    transition: background-position 0.3s;
    opacity: 0.3;
  }
  .product-center .item-background {
    width: 100%;
    height: 100%;
    position: absolute;
    border-radius: 10px;
    top: 0;
    background: linear-gradient(rgba(246,247,250,1), rgba(246,247,250,1)), url('/home/v2_rjdkha.png') no-repeat;
    background-position: 30% 80%;
    transition: background-position 0.3s;
    opacity: 0.2;
    /*background-image: url("/v2_rjdkha.png");*/
  }
  .product-center .active-item-background {
    opacity: 1;
    background: linear-gradient(rgba(0, 153, 255,0.9), rgba(0, 153, 255, 0.9)),  url('/home/v2_rjdkha.png') no-repeat  60% 10%;
    background-position: 30% 10%;
  }
</style>
