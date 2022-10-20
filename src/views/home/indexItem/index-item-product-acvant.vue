<template>
  <index-item-container background="#F7F7F7" min-title="我们的产品优势" title="星微联新一代关系型数据库">
    <div slot="content">
      <el-row v-for="(item, index) in userData" :key="'acvant' + index">
        <el-col :span="12" v-for="(childrenItem, childrenIndex) in item" :key="'acvantChildren' + childrenIndex" style="padding: 10px 15px;">
          <el-card >
            <div style="border-radius: 10px; padding: 20px; display: flex;" ref="itemContent" :style="{height: contentHeight === 0 ? 'unset' : contentHeight + 'px'}">
              <div style="padding-right: 20px;">
                <el-image style="width: 100px" :src="childrenItem.src"/>
              </div>
              <div>
                <div style="font-size: 26px; font-weight: 400">{{childrenItem.title}}</div>
                <div style="font-size: 16px; color: #101010; margin-top: 15px;">{{childrenItem.content}}</div>
              </div>
            </div>
          </el-card>
        </el-col>
      </el-row>
    </div>
  </index-item-container>
</template>

<script>
  import IndexItemContainer from "./index-item-container";
  import {getImageUrl} from "../../../util/util";
  export default {
    name: "index-item-product-acvant",
    components: {IndexItemContainer},
    data() {
      return {
        contentHeight: 0,
        data: [
          {
            title: "差动引擎",
            content: "采用良好兼容性的传统文件存储引擎技术不仅可以解决海量表数据的存储同时解决查询引擎效率问题。",
            src: getImageUrl('/home/v2_rijl23.png'),
          },
          {
            title: "高并发、高吞吐、接口高速访问",
            content: "SQL引擎100%兼容MYSQL;\nSQL引擎100%兼容MYSQL;\nSQL引擎100%兼容MYSQL",
            src: getImageUrl('/home/v2_rijl23.png'),
          },
          {
            title: "差分引擎",
            content: "采用可配置的内存数据冷热老化分级分离技术，实现单表逻辑空间的海量数据单一镜像管理（就是十、百、千亿级巨表不分片）。",
            src: getImageUrl('/home/v2_rijl23.png'),
          },
          {
            title: "跨硬件平台的平滑兼容能力",
            content: "采用Jvm技术开发的新一代数据库引擎，实现指令集级、系统级跨平台、MYSQL兼容指令生态，可直接使用MySQL驱动。",
            src: getImageUrl('/home/v2_rijl23.png'),
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
          this.contentHeight = height - 50;
        }, 30);
      }
    },
    mounted() {
      this.init();
    }
  }
</script>

<style scoped>

</style>
