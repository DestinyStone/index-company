<template>
  <div style="display: flex; justify-content: center;">
    <div style="width: 70%;">
      <regard-we-title title="企业介绍">
        <div style="display: flex; height: 350px;">
          <div style="background: #faf8fa; padding: 30px; font-size: 18px;">
            <div style="color: #101010; font-size: 28px; font-weight: 700;">公司简介</div>
            <p style="text-indent: 2em;"><span>        星徽联（上海）数据科技有限公司，成立于2021年05月25日，总部位于上海；同年6月24日，成立广州分公司。星徽联是一家汇聚了大数据专家，国际供应链专家，电子支付专家，算法与AI智能专家的数字化综合技术公司。</span></p>
            <p style="text-indent: 2em;"><span>        公司内部核心技术骨干团队自主研发的星徽Difference Methods Database数据库，AI视觉智能产品等数字化产品，大数据平台，为数字化社会转型的最后一公里建立创新，敏捷的数字化生态新环境。</span></p>
          </div>
          <div>
            <el-image style="height: 350px; width: 415px;" :src="getImageUrl('/home/v2_rjfamu.png')"></el-image>
          </div>
        </div>
      </regard-we-title>
      <regard-we-title title="荣誉资质">
        <div>
          <div style="display: flex;">
            <div v-for="item in minAuthData">
              <div>
                <div style="padding: 0 30px;">
                  <el-image :src="item.src"/>
                </div>
                <div style="height: 50px; line-height: 50px; text-align: center;">{{item.title}}</div>
              </div>
            </div>
          </div>
          <div style="display: flex; margin-top: 80px;">
            <div v-for="item in authData">
              <div>
                <div style="padding: 0 30px;">
                  <el-image :src="item.src"/>
                </div>
                <div style="height: 50px; line-height: 50px; text-align: center;">{{item.title}}</div>
              </div>
            </div>
          </div>
        </div>
      </regard-we-title>
      <regard-we-title title="新闻动态">
        <div>
          <el-row>
            <el-col :span="10">
              <el-card :style="{'height': journalHeight + 'px'}" style="cursor: pointer;" @click.native="handlerClickJournal(mainJournalData)">
                <div style="padding: 5px;">
                  <el-image :src="mainJournalData.imgSrc"></el-image>
                  <div>
                    <div style="height: 30px; line-height: 30px; padding: 20px; font-size: 20px;">新闻标题：{{mainJournalData.title}}</div>
                    <div style="padding: 0 20px; color: #808080;">摘要内容：{{mainJournalData.mainContent}}</div>
                    <div style="padding: 50px 20px 0 20px; color: #808080;">{{mainJournalData.year + '-' + mainJournalData.time}}</div>
                  </div>
                </div>
              </el-card>
            </el-col>
            <el-col :span="14">
              <div class="regard-we-journal-card" style="padding-left: 30px;">
                <div v-for="item in journalData"  style="padding-bottom: 10px;">
                  <el-card @click.native="handlerClickJournal(item)"  style="cursor: pointer;">
                   <div style="display: flex; justify-content: space-between;"  ref="journalCardItem">
                     <div style="display: flex;">
                       <div>
                         <el-image style="height: 90px;" :src="item.imgSrc"/>
                       </div>
                       <div style="display: flex; justify-content: center; flex-flow: column;">
                         <div style="padding-left: 50px;">
                           <div style="font-size: 18px; color: #101010; ">{{item.title}}</div>
                           <div style="font-size: 14px; color: #808080; margin-top: 15px;">摘要内容: {{item.mainContent}}</div>
                         </div>
                       </div>
                     </div>
                     <div style="display: flex; justify-content: center; flex-flow: column">
                       <div style="padding: 0 20px;">
                         <div style="color: #d1d1d1; font-size: 20px;">{{item.year}}</div>
                         <div style="color: #e6e6e6; font-size: 28px;">{{item.time}}</div>
                       </div>
                     </div>
                   </div>
                  </el-card>
                </div>
              </div>
            </el-col>
          </el-row>
        </div>
      </regard-we-title>
      <regard-we-title title="加入我们">
        <div>
          <div v-for="item in postData" style="background: #f9fafa; margin-bottom: 20px; padding: 0 20px;">
            <div style="display: flex; justify-content: space-between; border-bottom: 1px solid #EBEEF5; line-height: 45px; height: 45px">
              <div style="font-size: 18px; color: #101010; font-weight: 700">{{item.name}}</div>
              <div style="font-size: 14px; color: #808080; cursor: pointer;" v-if="item.isOpen === 0" @click="handlerSwitch(item, 1)">展开>></div>
              <div style="font-size: 14px; color: #808080; cursor: pointer;" v-if="item.isOpen === 1" @click="handlerSwitch(item, 0)">收起<<</div>
            </div>
            <div style="font-size: 16px; color: #525252;">
              <div  v-if="item.isOpen === 0" style="display: flex;  justify-content: space-between; line-height: 45px; height: 45px">
                <div>学历要求: {{item.askFor}}</div>
                <div>招聘人数: {{item.count}}</div>
                <div>工作年限: {{item.yearAskFor}}</div>
                <div>工作地点: {{item.address}}</div>
                <div>薪资福利: {{item.money}}</div>
                <div>更新时间: {{item.updateTime}}</div>
              </div>
              <div  v-if="item.isOpen === 1" style="padding: 15px 0;">
                <div style="font-size: 14px; line-height: 18px; min-height: 18px;" v-for="(contentItem, contentIndex) in item.detailContent.split('\n')" :key="contentIndex">{{contentItem}}</div>
              </div>
            </div>
          </div>
        </div>
      </regard-we-title>
      <regard-we-title title="联系我们">
        <div style="background: #f9fafa; padding: 20px;">
          <div style=" border-bottom: 1px solid #EBEEF5; padding-bottom: 35px;">
            <el-row>
              <el-col :span="12">
                <div>
                  <i class="el-icon-location" style="font-size: 30px; color: #2468F2"/>
                  <span style="font-size: 24px; color: #696969; font-weight: 700">上海总部</span>
                </div>
                <div style="color: #696969; font-size: 18px; line-height: 35px; margin-top: 20px; padding-left: 30px;">
                  <div>地址：上海浦东新区郭守敬路498号6幢14号楼14109室</div>
                  <div>总机：021-58593088</div>
                </div>
              </el-col>
              <el-col :span="12">
                <div>
                  <i class="el-icon-location" style="font-size: 30px; color: #2468F2"/>
                  <span style="font-size: 24px; color: #696969; font-weight: 700">广州分公司</span>
                </div>
                <div style="color: #696969; font-size: 18px; line-height: 35px; margin-top: 20px; padding-left: 30px;">
                  <div>地址：广东省广州市天河区大观南路12号润农商务中心主楼211</div>
                  <div>电话：020-58593088</div>
                </div>
              </el-col>
            </el-row>
          </div>
          <div style="color: #696969; font-size: 18px; line-height: 35px; margin-top: 30px;">
            <el-row>
              <el-col :span="12">
                <div>
                  <div>全国服务热线：15012345678(同微信号)</div>
                  <div>售前咨询：</div>
                  <div>销售服务邮箱：xxxxxxx@xxxxx.com</div>
                  <div>售后热线：</div>
                </div>
              </el-col>
              <el-col :span="12">
                <div>技术支持邮箱：xxxxxxx@xxxxx.com</div>
                <div>技术支持电话：15012345678</div>
              </el-col>
            </el-row>
          </div>
        </div>
      </regard-we-title>
    </div>
  </div>
</template>

<script>
  import RegardWeTitle from "./regard-we-title";
  import {getImageUrl} from "../../../../util/util";
  export default {
    name: "regard-we",
    components: {RegardWeTitle},
    data() {
      return {
        journalHeight: 0,
        mainJournalData: {imgSrc: getImageUrl('/home/v2_rjfds3.png'), title: "2022年集中式交易型数据库采购项目", mainContent: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx", year: "2022", time: "09-10"},
        journalData: [
          {imgSrc: getImageUrl('/home/v2_rjfdzo.png'), title: "2022年集中式交易型数据库采购项目", mainContent: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx", year: "2022", time: "09-10"},
          {imgSrc: getImageUrl('/home/v2_rjfdzo.png'), title: "2022年集中式交易型数据库采购项目", mainContent: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx", year: "2022", time: "09-10"},
          {imgSrc: getImageUrl('/home/v2_rjfdzo.png'), title: "2022年集中式交易型数据库采购项目", mainContent: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx", year: "2022", time: "09-10"},
          {imgSrc: getImageUrl('/home/v2_rjfdzo.png'), title: "2022年集中式交易型数据库采购项目", mainContent: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx", year: "2022", time: "09-10"},
          {imgSrc: getImageUrl('/home/v2_rjfdzo.png'), title: "2022年集中式交易型数据库采购项目", mainContent: "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx", year: "2022", time: "09-10"},
        ],
        minAuthData: [
          {
            src: getImageUrl('/home/v2_rjfaz1.jpg'),
            title: "XXXXX软件著作权登记证书"
          },
          {
            src: getImageUrl('/home/v2_rjfaz1.jpg'),
            title: "XXXXX软件著作权登记证书"
          },
          {
            src: getImageUrl('/home/v2_rjfaz1.jpg'),
            title: "XXXXX软件著作权登记证书"
          },
          {
            src: getImageUrl('/home/v2_rjfaz1.jpg'),
            title: "XXXXX软件著作权登记证书"
          }
        ],
        authData: [
          {
            src: getImageUrl('/home/v2_rjfazs.jpg'),
            title: "XXXXX软件著作权登记证书"
          },
          {
            src: getImageUrl('/home/v2_rjfazs.jpg'),
            title: "XXXXX软件著作权登记证书"
          },
          {
            src: getImageUrl('/home/v2_rjfazs.jpg'),
            title: "XXXXX软件著作权登记证书"
          },
        ],
        postData: [
          {
            isOpen: 0,
            name: "Java技术负责人",
            askFor: "本科",
            count: "2",
            yearAskFor: "1年以上",
            address: "广州",
            money: "面议",
            updateTime: "2022-09-12",
            detailContent: "岗位职责：\n" +
              "1、根据客户需求和公司行业解决方案开展售前工作。包括公司宣讲、数据库方案讲解、客户针对性方案制作及讲解，项目标书制作及讲标等工作内容；\n" +
              "2、与业务部门密切配合，快速挖掘客户需求与项目合作机会，推进数据库平台应用解决方案和数据库产品的业务拓展；\n" +
              "3、完善与提升公司在央企、军工、金融、政府、能源等行业的数据库解决方案。\n" +
              "\n" +
              "任职要求：\n" +
              "1、本科及以上学历，3年以上售前工作经历，有政府/金融/能源/军工等客户行业背景优先；\n" +
              "2、具备数据库产品应用经验，熟悉至少Oracle、PostgreSQL、SQLServer、MySQL等任意两种数据库的产品架构和应用；\n" +
              "3、具备项目管理、售前工作经验，熟悉项目招投标工作流程；能够快速理解客户业务需求能力，对行业未来业务发展、数据库应用场景有较为深刻的理解；\n" +
              "4、具备至少1年软件开发工作经验，熟悉Java、C#等至少一种语言的基本使用、了解常用软件开发框架、开发接口及软件开发的基本流程；\n" +
              "5、具有较强的方案能力，能够根据用户业务需求制定详细解决方案；\n" +
              "6、具有一定项目管理经验；\n" +
              "7、能接受短期出差。\n\n" +
              "简历请发送至邮箱： ehr@unstarstech.com"
          },
          {
            isOpen: 0,
            name: "Java技术负责人",
            askFor: "本科",
            count: "2",
            yearAskFor: "1年以上",
            address: "广州",
            money: "面议",
            updateTime: "2022-09-12",
            detailContent: "岗位职责：\n" +
              "1、根据客户需求和公司行业解决方案开展售前工作。包括公司宣讲、数据库方案讲解、客户针对性方案制作及讲解，项目标书制作及讲标等工作内容；\n" +
              "2、与业务部门密切配合，快速挖掘客户需求与项目合作机会，推进数据库平台应用解决方案和数据库产品的业务拓展；\n" +
              "3、完善与提升公司在央企、军工、金融、政府、能源等行业的数据库解决方案。\n" +
              "\n" +
              "任职要求：\n" +
              "1、本科及以上学历，3年以上售前工作经历，有政府/金融/能源/军工等客户行业背景优先；\n" +
              "2、具备数据库产品应用经验，熟悉至少Oracle、PostgreSQL、SQLServer、MySQL等任意两种数据库的产品架构和应用；\n" +
              "3、具备项目管理、售前工作经验，熟悉项目招投标工作流程；能够快速理解客户业务需求能力，对行业未来业务发展、数据库应用场景有较为深刻的理解；\n" +
              "4、具备至少1年软件开发工作经验，熟悉Java、C#等至少一种语言的基本使用、了解常用软件开发框架、开发接口及软件开发的基本流程；\n" +
              "5、具有较强的方案能力，能够根据用户业务需求制定详细解决方案；\n" +
              "6、具有一定项目管理经验；\n" +
              "7、能接受短期出差。\n\n" +
              "简历请发送至邮箱： ehr@unstarstech.com"
          },
          {
            isOpen: 0,
            name: "Java技术负责人",
            askFor: "本科",
            count: "2",
            yearAskFor: "1年以上",
            address: "广州",
            money: "面议",
            updateTime: "2022-09-12",
            detailContent: "岗位职责：\n" +
              "1、根据客户需求和公司行业解决方案开展售前工作。包括公司宣讲、数据库方案讲解、客户针对性方案制作及讲解，项目标书制作及讲标等工作内容；\n" +
              "2、与业务部门密切配合，快速挖掘客户需求与项目合作机会，推进数据库平台应用解决方案和数据库产品的业务拓展；\n" +
              "3、完善与提升公司在央企、军工、金融、政府、能源等行业的数据库解决方案。\n" +
              "\n" +
              "任职要求：\n" +
              "1、本科及以上学历，3年以上售前工作经历，有政府/金融/能源/军工等客户行业背景优先；\n" +
              "2、具备数据库产品应用经验，熟悉至少Oracle、PostgreSQL、SQLServer、MySQL等任意两种数据库的产品架构和应用；\n" +
              "3、具备项目管理、售前工作经验，熟悉项目招投标工作流程；能够快速理解客户业务需求能力，对行业未来业务发展、数据库应用场景有较为深刻的理解；\n" +
              "4、具备至少1年软件开发工作经验，熟悉Java、C#等至少一种语言的基本使用、了解常用软件开发框架、开发接口及软件开发的基本流程；\n" +
              "5、具有较强的方案能力，能够根据用户业务需求制定详细解决方案；\n" +
              "6、具有一定项目管理经验；\n" +
              "7、能接受短期出差。\n\n" +
              "简历请发送至邮箱： ehr@unstarstech.com"
          }
        ]
      }
    },
    methods: {
      handlerClickJournal(nows) {
        this.$emit("clickJournal", nows);
      },
      handlerSwitch(item, status) {
        if (!item.isOpen) {
          item.isOpen = 1;
        }
        this.$set(item, 'isOpen', status);
      },
      getJournalHeight() {
        let height = 0;
        for(let item of this.$refs['journalCardItem']) {
          height += item.offsetHeight;
        }
        this.journalHeight = height + 100;
      },
      getImageUrl(url) {
        return getImageUrl(url);
      }
    },
    mounted() {
      this.getJournalHeight();
    }
  }
</script>

<style>
  .regard-we-journal-card  .el-card__body {
    padding: 5px;
  }
</style>
