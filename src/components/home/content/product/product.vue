<template>
  <index-content-container class="product" style="padding-bottom: 100px;">
    <div style="margin-top: 40px; color: #101010; line-height: 30px">
      <div>LonglinDB 1.0</div>
      <div>我们专注于帮助企业基于 TiDB 数据库快速构建应用程序，使企业无需担心数据库的性能、性能抖动、安全、高可用、容灾、SQL 语句的性能问题排查等问题。在 6.3.0-DMR 版本中，你可以获得以下关键特性。</div>
      <div>
        <div style="display: flex;">
          <div>
            <i class="el-icon-success" style="color: #2468F2;"/>
          </div>
          <div style="margin-left: 10px;">
            TiKV 静态加密支持国密算法 SM4。
          </div>
        </div>
        <div style="display: flex;">
          <div>
            <i class="el-icon-success" style="color: #2468F2;"/>
          </div>
          <div style="margin-left: 10px;">
            TiDB 支持基于国密算法 SM3 插件的身份验证。
          </div>
        </div>
        <div style="display: flex;">
          <div>
            <i class="el-icon-success" style="color: #2468F2;"/>
          </div>
          <div style="margin-left: 10px;">
            SQL 语句 CREATE USER 和 ALTER USER 支持 ACCOUNT LOCK/UNLOCK 选项。
          </div>
        </div>
        <div style="display: flex;">
          <div>
            <i class="el-icon-success" style="color: #2468F2;"/>
          </div>
          <div style="margin-left: 10px;">
            TiDB 支持 Null-Aware Anti Join。
          </div>
        </div>
        <div style="display: flex;">
          <div>
            <i class="el-icon-success" style="color: #2468F2;"/>
          </div>
          <div style="margin-left: 10px;">
            TiDB 提供 SQL 查询执行时间的细粒度指标。
          </div>
        </div>
        <div style="display: flex;">
          <div>
            <i class="el-icon-success" style="color: #2468F2;"/>
          </div>
          <div style="margin-left: 10px;">
            分区表新增简化 Range 分区的语法糖。
          </div>
        </div>
        <div style="display: flex;">
          <div>
            <i class="el-icon-success" style="color: #2468F2;"/>
          </div>
          <div style="margin-left: 10px;">
            Range COLUMNS 分区方式支持定义多列。
          </div>
        </div>
      </div>
      <div>
        <div style="margin: 20px 35px; display: flex;">
          <div>请选择架构</div>
          <div style="margin-left: 10px;">
            <el-select size="mini" v-model="frameSelect" placeholder="请选择">
              <el-option
                  v-for="item in frameOptions"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value">
              </el-option>
            </el-select>
          </div>
        </div>
        <div>
          <div v-for="item in installData" style="margin-bottom: 20px;">
            <div style="padding: 15px 20px; border-radius: 5px; background: rgb(247, 248, 249); border: 1px solid rgb(211, 211, 211); display: flex; justify-content: space-between; width: 380px; height: 70px; font-size: 14px;">
              <div>
                <div>{{item.name}}</div>
                <div style="color: #8c8b8b; font-size: 12px;">{{item.remark}}</div>
              </div>
              <div style="display: flex; justify-content: center; flex-flow: column">
                <el-button type="primary" size="small">立即下载</el-button>
              </div>
            </div>
          </div>
        </div>
        <div>支持操作操作：Linux，Windows</div>
        <div class="btn-text">快速上手指南</div>
        <div class="btn-text">前往问答社区提问</div>
        <div class="btn-text">了解社区</div>
        <div class="btn-text">邮箱联系我们：support@unstarstech.com</div>
      </div>
    </div>
  </index-content-container>
</template>

<script>
  import IndexContentContainer from "../index-content-container";
  export default {
    name: "product",
    components: {IndexContentContainer},
    data() {
      return {
        frameSelect: '0',
        frameOptions: [{
          value: '0',
          label: 'X86,64-bit'
        }, {
          value: '1',
          label: 'ARM,64-bit'
        }],
        installData: [
          {
            name: "LonglinDB-communit-server  软件包",
            remark: "获取LonglinDB 一键安装离线包"
          },
          {
            name: "LonglinDB-communit-toolkit  软件包",
            remark: "获取LonglinDB 工具包"
          }
        ]
      }
    }
  }
</script>

<style scoped>
  .product .btn-text {
    margin-top: 5px;
    color: #2468F2;
    cursor: pointer;
  }
</style>
