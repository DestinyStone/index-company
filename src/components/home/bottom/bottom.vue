<template>
  <div style="width: 100%; height: 500px; background: #000431; color: #ffffff; display: flex; justify-content: center;">
    <div style="width: 80%; height: 500px; position: relative">
      <div style="padding-top: 60px;">
        <el-row>
          <el-col :span="6">
            <div style="display: flex;">
              <div>
                <el-image style="width: 50px" src="v2_rijl23.png"/>
              </div>
              <div style="padding-left: 10px;">
                <div style="font-size: 24px; white-space: nowrap">星微联（上海）数据科技有限公司</div>
                <div style="font-size: 16px; padding: 10px 0;">致力于数据库中国生态的耕耘与创新</div>
              </div>
            </div>
            <div style="margin-top: 20px;">
              <div v-for="item in letterData" style="padding: 5px 0; white-space: nowrap">
                {{item.title}}: {{item.content}}
              </div>
            </div>
          </el-col>
          <el-col :span="18">
            <div style="display: flex; justify-content: space-around;">
              <div v-for="item in selectData">
                <div style="font-size: 20px; margin-bottom: 8px; cursor: pointer;">{{item.title}}</div>
                <div style="padding: 3px 0;cursor: pointer;" v-for="contentItem in item.content">
                  <div v-if="contentItem.type === undefined || contentItem.type === 'text'">{{contentItem.title}}</div>
                  <div v-if="contentItem.type === 'img'" style="margin-top: 20px;">
                    <el-image style="width: 100px" :src="contentItem.src"></el-image>
                    <div>{{contentItem.title}}</div>
                  </div>
                </div>
              </div>
            </div>
          </el-col>
        </el-row>
      </div>
      <div style="border-top: 1px solid #c6c6c6; position: absolute; bottom: 0; width: 100%; padding: 30px; text-align: center;">
        <el-row>
          <el-col :span="8">
            Copyright © 2022 星徽联（上海）数据科技有限公司
          </el-col>
          <el-col :span="6">
            备案号：xxxxxxxxxx
          </el-col>
          <el-col :span="8">
            沪公网安备   XXXXXXXXXXX  号
          </el-col>
        </el-row>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "bottom",
    data() {
      return {
        letterData: [
          {
            title: "总部",
            content: "上海浦东新区郭守敬路498号6幢14号楼14109室"
          },
          {
            title: "分部",
            content: "广东省广州市天河区大观南路12号润农商务中心主楼211"
          },
          {
            title: "电话",
            content: "020-58593088"
          },
          {
            title: "技术支持",
            content: "技术支持：it@unstarstech.com"
          },
          {
            title: "售后热线",
            content: ""
          },
          {
            title: "售前咨询",
            content: ""
          }
        ],
        selectData: [
          {
            title: "关于我们",
            content: [
              {
                title: "企业介绍",
              },
              {
                title: "荣誉资质",
              },
              {
                title: "新闻动态",
              },
              {
                title: "加入我们",
              },
              {
                title: "联系我们",
              }
            ]
          },
          {
            title: "数库产品",
            content: [
              {
                title: "社区版",
              },
              {
                title: "企业版",
              },
              {
                title: "集团版",
              },
              {
                title: "物联版",
              },
              {
                title: "定制版",
              }
            ]
          },
          {
            title: "资源中心",
            content: [
              {
                title: "部署文件",
              },
              {
                title: "快速上手",
              },
              {
                title: "本地部署",
              },
              {
                title: "开发指南",
              },
              {
                title: "星微联公众号",
                type: "img",
                src: "v2_rjdpa5.jpg"
              }
            ]
          }
        ]
      }
    }
  }
</script>

<style scoped>

</style>
