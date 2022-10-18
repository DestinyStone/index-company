<template>
  <div>
    <bar>
      <div slot="content">
        <bar-title-select/>
      </div>
    </bar>
  </div>
</template>

<script>
  import bar from "./bar";
  import BarTitleSelect from "./bar-title-select";
  export default {
    name: "indexBar",
    components: {BarTitleSelect, bar}
  }
</script>

<style scoped>

</style>
