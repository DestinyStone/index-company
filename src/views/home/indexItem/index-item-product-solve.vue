<template>
  <index-item-container class="product-solve" background="#ffffff" title="解决方案">
    <div slot="content">
      <el-row>
        <el-col :span="6" v-for="(childrenItem, index) in data" :key="'childrenItem' + index">
          <div style="width: 100%; position:relative; " :style="{height: height + 'px'}" ref="solveItem" @mouseenter="activeIndex = index">
            <div style="position:relative; z-index:999; color: #ffffff;">
              <div class="product-solve-tag" :style="{top: height / 2 - (activeIndex === index ? 200 : 100) + 'px'}">
                <div>
                  <c-svg :type="childrenItem.svgType"/>
<!--                  <i style="font-size: 60px;" class="el-icon-user"/>-->
                  <div style="font-size: 25px; font-weight: 700; margin-top: 20px;">{{childrenItem.title}}</div>
                </div>
              </div>
              <div class="product-solve-content" :class="{'product-solve-content-active': activeIndex === index}" style="padding: 0 25px; line-height: 25px; position:absolute;" :style="{top: height / 2 - 50 + 'px', fontSize: fontSize + 'px'}">
                <div :style="{lineHeight: lineHeight + 'px'}">{{childrenItem.content}}</div>
                <div style="display: flex; justify-content: center; margin-top: 30px;">
                  <div class="concat-button">
                    了解更多
                    <i class="el-icon-right"/>
                  </div>
                </div>
              </div>
            </div>
            <div style="background: linear-gradient(rgba(0, 0, 0,0.3), rgba(0, 0, 0, 0.3)); z-index: 888;"  class="product-solve-img">

            </div>
            <div :style="getBackground(childrenItem.backgroundSrc)"  class="product-solve-img">

            </div>
          </div>
        </el-col>
      </el-row>
    </div>
  </index-item-container>
</template>

<script>
  import IndexItemContainer from "./index-item-container";
  import {getImageUrl} from "../../../util/util";
  import CSvg from "../svg/c-svg";
  export default {
    name: "index-item-product-solve",
    components: {CSvg, IndexItemContainer},
    data() {
      return {
        lineHeight: 30,
        fontSize: 18,
        activeIndex: -1,
        height: 0,
        data: [
          {
            svgType: "computer",
            title: "数字孪生",
            content: "元宇宙产业正在形成产业新浪潮，以建筑信息模型（Building Information Modeling, BIM）, 地理信息（Geographic Information, GIS）， 物联网信息（Internet of Thing）等多模合数据服务正在形成新的数据服务业态。",
            buttonText: "了解更多>>",
            backgroundSrc: "/home/v2_rijw6x.png",
          }, {
            svgType: "concat",
            title: "物联网",
            content: "物联网在工业行业里形成了新的产业需求， 新的多模包括了数据的采集与展示， 基础的数据分析与管理， 深度数据分析与应用， 工业控制。",
            buttonText: "了解更多>>",
            backgroundSrc: "/home/v2_rijx78.png",
          }, {
            svgType: "app",
            title: "数据智能",
            content: "轻量级高性能OLTP与OLAP引擎可以替换一部分依赖重量级的消息，大数据生态的流批一体数据智能生态。",
            buttonText: "了解更多>>",
            backgroundSrc: "/home/v2_rijxl0.png",
          }, {
            svgType: "money",
            title: "实时交易",
            content: "打造的智慧工厂注重实现数据一体化， 集成工业智能化管理系统， 打破了数据孤岛化现状，实现了设备可视化，打造智能工厂管控一体化平台和工业智能化管理平台",
            buttonText: "了解更多>>",
            backgroundSrc: "/home/v2_rijy9x.jpg",
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
        this.height = solve.offsetWidth * 2 < 500 ? 500 : solve.offsetWidth * 2;
        if (this.height < 800) {
          this.fontSize = 14;
          this.lineHeight = 20;
        }
      },
      getBackground(url) {
        return `background-image: url('${getImageUrl(url)}');`
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
