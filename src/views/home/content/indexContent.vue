<template>
  <div>
    <index-content-nav v-if="showBar" :data="navData" :bar-data="barData"/>
    <div v-if="indexKey === '/home'">
      <home/>
    </div>
    <div v-if="indexKey === '/regardWe'">
      <regard-we @clickJournal="handlerClickJournal"/>
    </div>
    <div v-if="indexKey === '/nows'">
      <journal/>
    </div>
    <div v-if="indexKey === '/product'">
      <product/>
    </div>
  </div>
</template>

<script>
  import IndexItemProductCenter from "../indexItem/index-item-product-center";
  import IndexItemProductAcvant from "../indexItem/index-item-product-acvant";
  import IndexItemProductSolve from "../indexItem/index-item-product-solve";
  import IndexItemProductFriend from "../indexItem/index-item-product-friend";
  import IndexItemProductConcat from "../indexItem/index-item-product-concat";
  import Home from "../home/home";
  import RegardWe from "./regardwe/regard-we";
  import IndexContentNav from "./index-content-nav";
  import Journal from "./journal/journal";
  import Product from "./product/product";
  export default {
    name: "indexContent",
    components: {
      Product,
      Journal,
      IndexContentNav,
      RegardWe,
      Home,
      IndexItemProductConcat,
      IndexItemProductFriend,
      IndexItemProductSolve, IndexItemProductAcvant, IndexItemProductCenter},
    props: {
      navData: {
        type: Array,
        default() {
          return []
        }
      },
      barData: {
        type: Array,
        default() {
          return []
        }
      },
      indexKey: {
        type: String,
      },
      showBar: {
        type: Boolean,
        default: false,
      }
    },
    methods: {
      handlerClickJournal(nows) {
        this.$emit("clickJournal", nows);
      },
    }
  }
</script>

<style scoped>

</style>
