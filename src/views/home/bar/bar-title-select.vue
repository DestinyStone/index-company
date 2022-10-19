<template>
  <div class="bar-title-select" @mouseout="handlermouseOver">
    <div v-for="(item, index) in data" ref="item"
         :key="'bar' + index" class="item"
         :class="{'select-item': activeIndex === index}"
         @click="handlerClick(item)"
         @mouseenter="handlerMouseEnterItem(item, index)">
      {{item.title}}
      <div class="item-children"
           :style="{
           'height': activeIndex === index ? (item.height ? item.height + 'px' : (childrenItemHeight * (item.children || []).length + 'px')) : '0',
           'left': (item.left || 0) + 'px',
           }">
        <div ref="item-children"
             :style="{ 'height': activeIndex === index ? (item.height ? item.height + 'px' : 'auto') : 'auto',}"
             :key="'bar-item' + childrenIndex"
             v-for="(childrenItem, childrenIndex) in (item.children || [])"
             :class="{'item-children-active': activeIndex === index && childrenIndex === activeItemIndex}"
             @click.stop="handlerClick(item, childrenItem)"
             @mousemove="isOver = false"
             @mouseenter.stop="handlerMouseEnterChildrenItem(childrenItem, childrenIndex, item)">
          <div v-if="childrenItem.slot === undefined || !childrenItem.slot">
            <div style="width: 3px; background: #409EFF"></div>
            {{childrenItem.title}}
          </div>
          <div v-if="childrenItem.slot" style="height: 300px">
            <slot :name="childrenItem.key"/>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "barTitleSelect",
    props: {
      data: {
        type: Array,
        default() {
          return []
        }
      }
    },
    data() {
      return {
        isOver: false,
        activeIndex: -1,
        activeItemIndex: -1,
        childrenItemHeight: 0,
      }
    },
    mounted() {
      this.getChildrenItemHeight();
      this.init();
    },
    methods: {
      init() {
      },
      handlerClick(parent, children) {
        if (parent.select === false) {
          return;
        }
        this.$emit("change", {parent, children});
      },
      handlermouseOver() {
        this.isOver = true;
        setTimeout(() => {
          if (this.isOver === true) {
            this.activeIndex = -1;
            this.activeItemIndex = -1;
          }
        }, 200)
      },
      handlerMouseEnterItem(item, index) {
        this.isOver = false;
        this.activeIndex = index;
        this.activeItemIndex = -1;

        if ((item.left === undefined) && item.children && item.children.length !== 0) {
          let parent = this.$refs['item'][index];
          let children = parent.getElementsByClassName("item-children")[0];
          item.left = (parent.offsetWidth - children.offsetWidth) / 2;
        }
      },
      handlerMouseEnterChildrenItem(item, index, parent) {
        setTimeout(() => {
          this.isOver = false;
          if (parent.select === false) {
            return;
          }
          this.activeItemIndex = index;
        }, 10)

      },
      getChildrenItemHeight() {
        let item = this.$refs['item-children'] && this.$refs['item-children'][0] || {};
        this.childrenItemHeight = item.offsetHeight;
      },
    }
  }
</script>

<style>
  .bar-title-select {
    display: flex;
    text-align: center;
  }
  .bar-title-select .item {
    padding: 0 50px;
    font-size: 15px;
    font-weight: 700;
    cursor: pointer;
    position: relative;
    z-index: 999;
  }
  .bar-title-select .select-item {
    color: #409EFF;
  }
  .bar-title-select .item-children {
    position: absolute;
    height: 0;
    z-index: 999;
    width: unset;
    max-width: unset;
    max-height: 300px;
    overflow: hidden;
    transition: height 0.5s;
  }
  .bar-title-select .item-children-mouse-enter {
    height: 300px;
  }
  .bar-title-select .item-children > div {
    height: 40px;
    padding: 0 15px;
    line-height: 40px;
    font-size: 15px;
    font-weight: 300;
    white-space:nowrap;
    background: rgba(0, 0, 0, 0.5);
    color: #ffffff;
  }
  .bar-title-select .item-children-active {
    background: rgba(64,158,255, 0.7) !important;
  }
</style>
