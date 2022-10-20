<template>
  <div  style="min-width: 1200px;">
    <bar>
      <div slot="title" style="display: flex; justify-content: center;">
        <div  style="font-size: 20px; font-weight: 700; display: flex; flex-flow: column; justify-content: center;">
          <div style="display: flex; margin-top: 15px;">
            <el-image style="width: 50px; height: 50px;" :src="getImageUrl('/home/v2_rihkmy.png')"/>
            <div style="line-height: 50px; height: 50px; margin-left: 20px; white-space: nowrap">星微联LonglinDB</div>
          </div>
        </div>
      </div>
      <div slot="content">
        <bar-title-select @change="handlerChange" :data="data">
          <div slot="/product/service">
            <div style="min-height: 300px !important; height: 300px !important; width: 700px; text-align: left; white-space: pre-wrap">
              <div>商业产品及服务</div>
              <div>
                <el-row>
                  <el-col :span="8">
                    <div style="padding-right: 10px;">
                      <div style="color: #cccccc;">
                        产品订阅
                      </div>
                      <div style="line-height: 22px;">星微联为企业客户提供产品订阅，通过该服务你可以获得完整的产品支持，持续的产品能力更新，周全而专业的产品支持专家经验赋能以及对你关键系统运行的可靠保障
                      </div>
                    </div>
                  </el-col>
                  <el-col :span="8">
                    <div style="color: #cccccc;">
                      专家咨询服务
                    </div>
                    <div style="line-height: 22px;">
                      星微联专家咨询服务为已购买产品订阅的企业用户提供咨询规划， 方案设计， 变更保障，诊断与优化，经验传递等一系列专业服务
                    </div>
                  </el-col>
                  <el-col :span="8">
                    <div style="padding-left: 10px;">
                      <div style="color: #cccccc;">
                        专业培训服务
                      </div>
                      <div style="line-height: 22px;">
                        提供面向重点行业客户的星微联MBD定制化内容开发和交付服务，助力客户数字化转型和新业务增长
                      </div>
                    </div>
                  </el-col>
                </el-row>
              </div>
              <div>
                <el-button type="primary"  style="margin-top: 35px;">联系我们</el-button>
              </div>
            </div>
          </div>
        </bar-title-select>
      </div>
      <div slot="phone">
        <div style="white-space: nowrap">
          <i class="el-icon-phone" style="font-size: 20px;"/>
          全国服务热线电话: 15012345678(同微信号)
        </div>
      </div>
    </bar>
  </div>
</template>

<script>
  import bar from "./bar";
  import BarTitleSelect from "./bar-title-select";
  import {getImageUrl} from "../../../util/util";
  export default {
    name: "indexBar",
    props: {
      data: {
        type: Array,
        default() {
          return []
        }
      },
    },
    components: {BarTitleSelect, bar},
    methods: {
      handlerChange(data) {
        this.$emit("change", data);
      },
      getImageUrl(url) {
        return getImageUrl(url);
      }
    }
  }
</script>

<style scoped>

</style>
