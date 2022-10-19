<template>
  <div>
    <div style="padding: 30px 0 10px 0; font-size: 25px; font-weight: 700; border-bottom: 1px solid #EBEEF5; position: relative">
      <div>
        {{title}}
        <div style="position:absolute; bottom: -2.5px; width: 50px; height: 5px; background: #2468F2">
        </div>
      </div>
    </div>
    <div style="padding: 50px 0 30px 0;">
      <slot/>
    </div>
  </div>
</template>

<script>
  export default {
    name: "regard-we-title",
    props: {
      title: {
        type: String,
      }
    },
    data() {
      return {

      }
    }
  }
</script>

<style scoped>

</style>
