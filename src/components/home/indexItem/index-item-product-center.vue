<template>
  <index-item-container class="product-center" background="#ffffff" min-title="产品中心" title="星微联关系数据库">
    <div slot="content">
      <el-row v-for="item in userData">
        <el-col :span="12" v-for="childrenItem in item" style="padding: 10px 15px;">
          <div style="position:relative;" @mouseenter="activeIndex = childrenItem.id">
            <div class="item" style="border: 1px solid #F2F6FC; border-radius: 10px; padding: 20px;">
              <div style="font-size: 26px; color: #2468F2; font-weight: 700">{{childrenItem.title}}</div>
              <pre class="item-content" :class="{'item-content-active': activeIndex === childrenItem.id}">{{childrenItem.content}}</pre>
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
        activeIndex: -1,
        data: [
          {
            id: "1",
            title: "社区版",
            content: "SQL引擎100%兼容MYSQL;\n采用存储和计算分离的架构解决云存储资源IO效率低下行业难题;\n提供实时级的内存升降级，秒级的故障恢复，全局数据一致性和兼容的数据备份容灾服务;",
            buttonText: "免费下载",
          },
          {
            id: "2",
            title: "企业版",
            content: "SQL引擎100%兼容MYSQL;\n采用存储和计算分离的架构解决云存储资源IO效率低下行业难题;\n提供实时级的内存升降级，秒级的故障恢复，全局数据一致性和兼容的数据备份容灾服务;",
            buttonText: "查看详情",
          },
          {
            id: "3",
            title: "数字孪生物联版",
            content: "提供可计量的工业数据点访问效率，提供稳定10ms/10亿行的高并发读取效率;\n采用Jvm技术开发的新一代数据库引擎, 数据库约3MB的jar文件大小;\n提供MySQL的一致兼容性，可直接使用MySQL的JDBC驱动包;",
            buttonText: "查看详情",
          },
          {
            id: "4",
            title: "定制版",
            content: "提供专用数据库内制业务函数定制;\n提供专用数据库内制的算法函数定制;\n提供专用数据库内置的SQL指令定制与独立优化;",
            buttonText: "立即咨询",
          }
        ]
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
  .product-center .item {
    position:relative;
    z-index: 999;
  }
  .product-center .item-content{
    font-size: 16px;
    color: #101010;
    margin-top: 15px;
  }
  .product-center .item-content-active {
    color: #ffffff !important;
  }
  .product-center .item-background {
    width: 100%;
    height: 100%;
    position: absolute;
    border-radius: 10px;
    top: 0;
    background: linear-gradient(rgba(102,204,255,0.7), rgba(102,204,255, 0.7)), url('/v2_rjdkha.png') no-repeat;
    background-position: 30% 80%;
    transition: background-position 0.3s;
    opacity: 0.2;
    /*background-image: url("/v2_rjdkha.png");*/
  }
  .product-center .active-item-background {
    opacity: 1;
    background: linear-gradient(rgba(0, 153, 255,0.7), rgba(0, 153, 255, 0.7)),  url('/v2_rjdkha.png') no-repeat  60% 10%;
    background-position: 30% 10%;
  }
</style>
