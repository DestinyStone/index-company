<template>
  <div>
    <index-bar/>
    <carousel/>
  </div>
</template>

<script>
  import IndexBar from "./bar/index-bar";
  import Carousel from "./carousel/carousel";
  export default {
    name: "index",
    components: {Carousel, IndexBar}
  }
</script>

<style scoped>

</style>
