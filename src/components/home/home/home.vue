<template>
  <div>
    <index-item-product-center/>
    <index-item-product-acvant/>
    <index-item-product-solve/>
    <index-item-product-friend/>
    <index-item-product-concat/>
  </div>
</template>

<script>
  import IndexItemProductCenter from "../indexItem/index-item-product-center";
  import IndexItemProductAcvant from "../indexItem/index-item-product-acvant";
  import IndexItemProductSolve from "../indexItem/index-item-product-solve";
  import IndexItemProductFriend from "../indexItem/index-item-product-friend";
  import IndexItemProductConcat from "../indexItem/index-item-product-concat";
  export default {
    name: "home",
    components: {
      IndexItemProductConcat,
      IndexItemProductFriend,
      IndexItemProductSolve, IndexItemProductAcvant, IndexItemProductCenter},
  }
</script>

<style scoped>

</style>
