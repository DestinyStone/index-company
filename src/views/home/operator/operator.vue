<template>
  <div class="index-operator" :style="{'top': topHeight + 'px'}">
    <div class="btn" @click.stop="handlerClick('person')">
      <div style="display: flex; justify-content: center;">
        <el-image style="height: 35px; width: 35px; margin-top: 10px;" :src="getImageUrl('/home/person.png')"/>
      </div>
      <div class="init-width" @click.stop :class="{'active-width': clickKey === 'person'}" style="position:absolute; top: 0; right: 61px; z-index: 888; width: 200px; background: #ffffff">
        <div class="background" style="display: flex; width: 200px; height: 50px; line-height: 50px;">
          <svg style="width: 24px; height: 24px; margin-top: 13px; margin-left: 20px; fill: #2468F2" xmlns="http://www.w3.org/2000/svg" class="styles__StyledSVGIconPathComponent-sc-16fsqc8-0 chVtzI svg-icon-path-icon fill" viewBox="0 0 32 32" width="24" height="24"><defs data-reactroot=""></defs><g><path d="M28 10.667c1.473 0 2.667 1.194 2.667 2.667v0 5.333c0 1.473-1.194 2.667-2.667 2.667v0h-1.416c-0.686 5.289-5.163 9.333-10.584 9.333v0-2.667c4.418 0 8-3.582 8-8v0-8c0-4.418-3.582-8-8-8s-8 3.582-8 8v0 9.333h-4c-1.473 0-2.667-1.194-2.667-2.667v0-5.333c0-1.473 1.194-2.667 2.667-2.667v0h1.416c0.687-5.289 5.163-9.332 10.584-9.332s9.897 4.043 10.578 9.278l0.006 0.054h1.416zM10.347 21.047l1.413-2.261c1.199 0.762 2.66 1.215 4.227 1.215 0.005 0 0.009 0 0.014 0h-0.001c0.004 0 0.008 0 0.013 0 1.567 0 3.028-0.453 4.26-1.234l-0.032 0.019 1.413 2.261c-1.599 1.017-3.548 1.62-5.637 1.62-0.006 0-0.011 0-0.017 0h0.001c-0.005 0-0.011 0-0.016 0-2.089 0-4.038-0.604-5.68-1.646l0.043 0.026z"></path></g></svg>
          <div style="margin-left: 15px; font-size: 18px; color: #101010;">星微联 客服1</div>
        </div>
        <div class="background" style="display: flex; width: 200px; height: 50px; line-height: 50px; ">
          <svg style="width: 24px; height: 24px; margin-top: 13px; margin-left: 20px; fill: #2468F2"  xmlns="http://www.w3.org/2000/svg" class="styles__StyledSVGIconPathComponent-sc-16fsqc8-0 chVtzI svg-icon-path-icon fill" viewBox="0 0 32 32" width="24" height="24"><defs data-reactroot=""></defs><g><path d="M28 10.667c1.473 0 2.667 1.194 2.667 2.667v0 5.333c0 1.473-1.194 2.667-2.667 2.667v0h-1.416c-0.686 5.289-5.163 9.333-10.584 9.333v0-2.667c4.418 0 8-3.582 8-8v0-8c0-4.418-3.582-8-8-8s-8 3.582-8 8v0 9.333h-4c-1.473 0-2.667-1.194-2.667-2.667v0-5.333c0-1.473 1.194-2.667 2.667-2.667v0h1.416c0.687-5.289 5.163-9.332 10.584-9.332s9.897 4.043 10.578 9.278l0.006 0.054h1.416zM10.347 21.047l1.413-2.261c1.199 0.762 2.66 1.215 4.227 1.215 0.005 0 0.009 0 0.014 0h-0.001c0.004 0 0.008 0 0.013 0 1.567 0 3.028-0.453 4.26-1.234l-0.032 0.019 1.413 2.261c-1.599 1.017-3.548 1.62-5.637 1.62-0.006 0-0.011 0-0.017 0h0.001c-0.005 0-0.011 0-0.016 0-2.089 0-4.038-0.604-5.68-1.646l0.043 0.026z"></path></g></svg>
          <div style="margin-left: 15px; font-size: 18px; color: #101010;">星微联 客服1</div>
        </div>
      </div>
    </div>
    <div class="btn" @click.stop="handlerClick('service')" style="margin-top: 2px;">
      <div style="display: flex; justify-content: center;">
        <el-image style="height: 35px; width: 35px; margin-top: 10px;" :src="getImageUrl('/home/phone.png')"/>
      </div>
      <div class="init-width" @click.stop :class="{'active-width': clickKey === 'service'}" style="position:absolute; top: 0; right: 61px; z-index: 888; width: 200px;">
        <div class="background" style="display: flex; width: 200px; height: 50px; line-height: 50px;">
          <div style="margin-left: 15px; font-size: 18px; color: #101010;">电话:15923451234</div>
        </div>
        <div class="background" style="display: flex; width: 200px; height: 50px; line-height: 50px;">
          <div style="margin-left: 15px; font-size: 18px; color: #101010;">电话:15923451234</div>
        </div>
      </div>
    </div>
    <div class="btn wechat-btn" @click.stop="handlerClick('wechat')">
      <el-popover
          popper-class="wechat-el-popover"
          placement="left"
          trigger="click"
          :value="clickKey === 'wechat'"
      >
        <div style="width: 80px; height: 80px;">
          <el-image style="width: 80px" :src="getImageUrl('/home/v2_rjdpa5.jpg')"/>
        </div>
        <div style="display: flex; justify-content: center;" slot="reference">
          <el-image style="height: 35px; width: 35px; margin-top: 10px;" :src="getImageUrl('/home/wechat.png')"/>
        </div>
      </el-popover>
    </div>
    <div class="btn" style="margin-top: 1px;">
      <div style="text-align: center;" @click="handlerClickTop">
        <div style="height: 5px; line-height: 30px">
          <i class="el-icon-arrow-up"/>
        </div>
        TOP
      </div>
    </div>
  </div>
</template>

<script>
  import {getImageUrl} from "../../../util/util";
  import CSvg from "../svg/c-svg";

  export default {
    name: "operator",
    components: {CSvg},
    data() {
      return {
        clickKey: "",
        topHeight: 0,
      }
    },
    methods: {
      handlerClick(key) {
        this.clickKey = this.clickKey === key ? "" : key;
      },
      handlerClickTop() {
        window.scrollTo(0, 0);
      },
      getImageUrl(url) {
        return getImageUrl(url);
      }
    },
    mounted() {
      this.topHeight =  window.innerHeight / 2;
      document.body.addEventListener('click', () => {
        this.clickKey = "";
        console.log(33);
      })
    }
  }
</script>

<style>
  .index-operator {
    position: fixed;
    z-index: 999;
    right: 0;
    color: #2468F2;
    background: #ffffff;
  }
  .index-operator .init-width {
    width: 0;
    max-width: 0;
    overflow: hidden;
    transition: max-width 0.5s;
  }
  .index-operator .active-width {
    max-width: 200px;
  }
  .index-operator .btn {
    width: 60px;
    height: 60px;
    line-height: 60px;
    cursor: pointer;
    background: #ffffff;
    box-shadow: rgb(0 0 0 / 10%) 0px 2px 10px 0px;
    text-align: center;
    position: relative;
    margin-bottom: 1px;
  }
  .index-operator .background {
    box-shadow: rgb(0 0 0 / 10%) 0px 2px 10px 0px;
    background: #ffffff;
    border: 1px solid #F2F6FC;
  }
  .wechat-el-popover {
    min-width: unset !important;
  }
</style>
