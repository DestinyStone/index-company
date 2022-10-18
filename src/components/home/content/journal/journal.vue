<template>
    <index-content-container style="padding-bottom: 200px;">
      <el-row>
        <el-col :span="18">
          <div style="font-size: 26px; color: #101010; border-bottom: 1px solid #EBEEF5; line-height: 80px; height: 80px; text-align: center;">
            党建和创正式启动，打造移动云国产数据库标杆！
          </div>
          <div style="display: flex; font-size: 16px; color: #ababab; line-height: 50px; height: 50px; border-bottom: 1px solid #EBEEF5; ">
            <div style="margin-left: 10px;">时间：2022-09-20</div>
            <div style="margin-left: 80px;">来源：原创文章</div>
            <div style="margin-left: 80px;">浏览量：234</div>
          </div>
          <div style="color: #101010; font-size: 16px;">
            <p style="text-indent:2em;">
              作为高度创新型企业，不仅产品和业务要持续创新，党建工作也同样要求新求变。高效新颖的党建模式，不仅可以规避形式主义陷阱，还能有效带动企业业务多维发展。
            </p>
            <div style="display: flex; justify-content: center; padding: 30px 0;">
              <div>
                <el-image style="height: 230px;" src="v2_rjff57.png"/>
                <div style="text-align: center; line-height: 30px; height: 30px;">党总支书记王婷</div>
              </div>
            </div>
            <p style="text-indent:2em;"> 2022年9月1日，“移动云国产数据库标杆打造”党建和创启动会拉开帷幕，本次启动会由产品技术中心党支部和中移（苏州）软件技术有限公司（以下简称“移动云”）平台服务部第二党支部联合举办。活动旨在结合双方的企业特质和合作基础，将移动云数据库打造为国产数据库标杆！</p>
            <p>三跨五同步，实现党业双向融合</p>
            <p>启动会上，双方共同确定了党建和创的具体内容：即以互联共享为基础，以互促共赢为目标，实现“党业双向融合”，通过“三跨五同步”模式，实现跨区域、跨单位、跨领域的联合贯通，推动理论同学、组织同建、服务同行、品牌同筑、成效同享。</p>
          </div>
        </el-col>
        <el-col :span="6">
          <div style="padding-left: 30px;">
            <div style="font-size: 18px; color: #101010; border-bottom: 1px solid #EBEEF5; line-height: 120px; height: 80px; ">
              最新咨询
            </div>
            <div v-for="item in journalData" style="font-size: 14px; padding: 10px 0; height: 75px;  border-bottom: 1px solid #EBEEF5; display: flex; flex-flow: column; justify-content: space-between">
              <div>{{item.title}}</div>
              <div style="color: #ababab;">{{item.year + '-' + item.time}}</div>
            </div>
          </div>
        </el-col>
      </el-row>
    </index-content-container>
</template>

<script>
  import IndexContentContainer from "../index-content-container";
  export default {
    name: "journal",
    components: {IndexContentContainer},
    data() {
      return {
        journalData: [
          {imgSrc: "v2_rjfdzo.png", title: "2022年集中式交易型数据库采购项目", mainContent: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx", year: "2022", time: "09-10"},
          {imgSrc: "v2_rjfdzo.png", title: "2022年集中式交易型数据库采购项目", mainContent: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx", year: "2022", time: "09-10"},
          {imgSrc: "v2_rjfdzo.png", title: "2022年集中式交易型数据库采购项目", mainContent: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx", year: "2022", time: "09-10"},
          {imgSrc: "v2_rjfdzo.png", title: "2022年集中式交易型数据库采购项目", mainContent: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx", year: "2022", time: "09-10"},
          {imgSrc: "v2_rjfdzo.png", title: "2022年集中式交易型数据库采购项目", mainContent: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx", year: "2022", time: "09-10"},
        ],
      }
    }
  }
</script>

<style scoped>

</style>
