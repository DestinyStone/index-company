<template>
  <index-item-container class="product-solve" background="#ffffff" title="解决方案">
    <div slot="content">
      <el-row>
        <el-col :span="6" v-for="(childrenItem, index) in data">
          <div style="width: 100%; position:relative; " :style="{height: height + 'px'}" ref="solveItem" @mouseenter="activeIndex = index">
            <div style="position:relative; z-index:999; color: #ffffff;">
              <div class="product-solve-tag" :style="{top: height / 2 - (activeIndex === index ? 200 : 100) + 'px'}">
                <div>
                  <i style="font-size: 60px;" class="el-icon-user"/>
                  <div style="font-size: 25px; font-weight: 700; margin-top: 20px;">{{childrenItem.title}}</div>
                </div>
              </div>
              <div class="product-solve-content" :class="{'product-solve-content-active': activeIndex === index}" style="padding: 0 25px; line-height: 25px; position:absolute;" :style="{top: height / 2 - 50 + 'px'}">
                <div>{{childrenItem.content}}</div>
                <div style="display: flex; justify-content: center; margin-top: 30px;">
                  <div class="concat-button">
                    了解更多
                    <i class="el-icon-right"/>
                  </div>
                </div>
              </div>
            </div>
            <div style="background: linear-gradient(rgba(0, 153, 255,0.3), rgba(0, 153, 255, 0.3)); z-index: 888;"  class="product-solve-img">

            </div>
            <div style="background-image: url('v2_rijy9x.jpg');"  class="product-solve-img">

            </div>
          </div>
        </el-col>
      </el-row>
    </div>
  </index-item-container>
</template>

<script>
  import IndexItemContainer from "./index-item-container";
  export default {
    name: "index-item-product-solve",
    components: {IndexItemContainer},
    data() {
      return {
        activeIndex: -1,
        height: 0,
        data: [
          {
            title: "实时交易",
            content: "打造的智慧工厂注重实现数据一体化， 集成工业智能化管理系统， 打破了数据孤岛化现状，实现了设备可视化，打造智能工厂管控一体化平台和工业智能化管理平台",
            buttonText: "了解更多>>",
          }, {
            title: "实时交易",
            content: "打造的智慧工厂注重实现数据一体化， 集成工业智能化管理系统， 打破了数据孤岛化现状，实现了设备可视化，打造智能工厂管控一体化平台和工业智能化管理平台",
            buttonText: "了解更多>>",
          }, {
            title: "实时交易",
            content: "打造的智慧工厂注重实现数据一体化， 集成工业智能化管理系统， 打破了数据孤岛化现状，实现了设备可视化，打造智能工厂管控一体化平台和工业智能化管理平台",
            buttonText: "了解更多>>",
          }, {
            title: "实时交易",
            content: "打造的智慧工厂注重实现数据一体化， 集成工业智能化管理系统， 打破了数据孤岛化现状，实现了设备可视化，打造智能工厂管控一体化平台和工业智能化管理平台",
            buttonText: "了解更多>>",
          },
        ]
      }
    },
    mounted() {
      this.getHeight();
    },
    methods: {
      getHeight() {
        let solve = this.$refs['solveItem'] &&  this.$refs['solveItem'][0] || {};
        console.log(solve.offsetWidth);
        this.height = solve.offsetWidth * 2;
      },
      getBackground(url) {
        console.log(`linear-gradient(rgba(0, 153, 255,0.7), rgba(0, 153, 255, 0.7)),  url('${url}') no-repeat  100% 100%`)
        return `linear-gradient(rgba(0, 153, 255,0.7), rgba(0, 153, 255, 0.7)),  url('${url}') no-repeat`
      }
    },
    computed: {
      userData() {
        if (this.data.length === 4) {
          return [[this.data[0], this.data[1]], [this.data[2], this.data[3]]];
        }
        return [];
      }
    }
  }
</script>

<style scoped>
  .product-solve .product-solve-tag {
    text-align: center;
    position:absolute;
    width: 100%;
    height: 100%;
    transition: top 0.3s;
  }
  .product-solve .concat-button {
    width: 150px;
    height:  45px;
    line-height: 45px;
    background: #2468F2;
    text-align: center;
    color: #ffffff;
    font-size: 16px;
    cursor: pointer;
  }
  .product-solve .product-solve-content {
    opacity: 0;
    transition: opacity 0.3s;
  }
  .product-solve .product-solve-content-active {
    opacity: 1;
  }
  .product-solve .product-solve-img {
    background-size: 100% 100%;
    width: 100%;
    height: 100%;
    position:absolute;
    top: 0; left: 0;
  }
</style>
