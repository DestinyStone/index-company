<template>
  <div class="bar-title-select">
    <div v-for="(item, index) in data" ref="item" :key="'bar' + index" class="item" :class="{'select-item': activeIndex === index}" @mouseenter="handlerMouseEnterItem(item, index)">
      {{item.title}}
      <div class="item-children"
           :style="{
           'height': activeIndex === index ? childrenItemHeight * (item.children || []).length + 'px' : '0',
           'left': -(item.left - 80  || 0) + 'px'
           }">
        <div ref="item-children"
             :key="'bar-item' + childrenIndex"
             v-for="(childrenItem, childrenIndex) in (item.children || [])"
             :class="{'item-children-active': activeIndex === index && childrenIndex === activeItemIndex}"
             @mouseenter.stop="handlerMouseEnterChildrenItem(childrenItem, childrenIndex)">
          <div>
            <div style="width: 3px; background: #409EFF"></div>
            {{childrenItem.title}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "barTitleSelect",
    data() {
      return {
        activeIndex: -1,
        activeItemIndex: -1,
        data: [
          {
            title: "首页",
            children: [],
          },
          {
            title: "产品",
            children: [
              {
                title: "社区版"
              },
              {
                title: "企业版本"
              },
            ]
          },
          {
            title: "解决方案",
            children: [
              {
                title: "物联网解决方案111111111111"
              },
              {
                title: "物联网解决方案"
              },
            ]
          },
          {
            title: "关于我们",
            children: [
              {
                title: "企业介绍"
              },
              {
                title: "企业介绍"
              },
            ]
          },
          {
            title: "文档",
            children: [],
          }
        ],
        childrenItemHeight: 0,
      }
    },
    mounted() {
      this.getChildrenItemHeight();
    },
    methods: {
      handlermouseOver() {
        this.activeIndex = -1;
        this.activeItemIndex = -1;
      },
      handlerMouseEnterItem(item, index) {
        this.activeIndex = index;
        this.activeItemIndex = -1;
        if (!item.left && item.children && item.children.length !== 0) {
          item.left = this.$refs['item'][index].getElementsByClassName("item-children")[0].offsetWidth / 2;
        }
      },
      handlerMouseEnterChildrenItem(item, index) {
        this.activeItemIndex = index;
      },
      getChildrenItemHeight() {
        let item = this.$refs['item-children'] && this.$refs['item-children'][0] || {};
        this.childrenItemHeight = item.offsetHeight;
      },
      getChildrenItemLeftPos(event) {
        console.log(event);
        return "10px"
      }
    }
  }
</script>

<style scoped>
  .bar-title-select {
    display: flex;
    text-align: center;
  }
  .bar-title-select .item {
    padding: 0 30px;
    font-size: 15px;
    font-weight: 700;
    cursor: pointer;
    position: relative;
  }
  .bar-title-select .select-item {
    color: #409EFF;
  }
  .bar-title-select .item-children {
    position: absolute;
    height: 0;
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
    height: 35px;
    padding: 0 10px;
    line-height: 35px;
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
