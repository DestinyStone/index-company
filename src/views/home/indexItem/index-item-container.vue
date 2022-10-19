<template>
  <div class="index-item-container" :style="{background: background}">
    <div style="width: 70%">
      <div style="padding-top: 30px;">
        <div class="title-text" style="font-size: 20px; color:#666;" v-if="minTitlePosition === 'top'">{{minTitle}}</div>
        <div class="title-text" style="font-size: 30px; font-weight: 700">{{title}}</div>
        <div class="title-text" style="font-size: 20px; color:#666;" v-if="minTitlePosition === 'bottom'">{{minTitle}}</div>
      </div>
      <div style="padding: 35px 0;">
        <slot name="content"/>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "indexItemContainer",
    props: {
      background: {
        type: String,
      },
      minTitle: {
        type: String,
      },
      title: {
        type: String,
      },
      minTitlePosition: {
        type: String,
        default: "top",
      }
    },
    data() {
      return {

      }
    }
  }
</script>

<style scoped>
  .index-item-container {
    width: 100%;
    display: flex;
    justify-content: center;
  }
  .index-item-container .title-text {
    text-align: center;
    padding: 8px;
  }
</style>
