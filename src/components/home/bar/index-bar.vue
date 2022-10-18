<template>
  <div>
    <bar>
      <div slot="title" style="font-size: 20px; font-weight: 700">
        星微联LonglinDB
      </div>
      <div slot="content">
        <bar-title-select @change="handlerChange" :data="data"/>
      </div>
      <div slot="phone">
        <div>
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
      }
    }
  }
</script>

<style scoped>

</style>
