<template>
  <div class="sfc-tabbar" :class="{
      'is-fixed': fixed
    }">
    <slot></slot>
  </div>
</template>

<script>
/**
 * sfc-tabbar
 * @module components/tabbar
 * @desc 底部 tab，依赖 tab-item
 * @param {boolean} [fixed=false] - 固定底部
 * @param {*} value - 返回 item component 传入的 id
 *
 * @example
 * <sfc-tabbar v-model="selected">
 *   <sfc-tab-item id="订单">
 *     <img slot="icon" src="http://placehold.it/100x100">
 *     <span slot="label">订单</span>
 *   </sfc-tab-item>
 * </sfc-tabbar>
 *
 * <sfc-tabbar v-model="selected" fixed>
 *   <sfc-tab-item :id="['传入数组', '也是可以的']">
 *     <img slot="icon" src="http://placehold.it/100x100">
 *     <span slot="label">订单</span>
 *   </sfc-tab-item>
 * </sfc-tabbar>
 */
export default {
  name: 'sfc-tabbar',

  props: {
    fixed: Boolean,
    value: {}
  }
};
</script>

<style lang="css">
  @import "../../../src/style/var.css";

  @component-namespace sfc {
    @component tabbar {
      background-image:linear-gradient(180deg, $color-grey, $color-grey 50%, transparent 50%);
      background-size: 100% 1px;
      background-repeat: no-repeat;
      background-position: top left;
      position: relative;
      background-color: $tabbar-background-color;
      display: flex;
      position: absolute * 0 0 0;
      text-align: center;

      @when fixed {
        position: fixed * 0 0 0;
        z-index: $z-index-normal;
      }

      > .sfc-tab-item.is-selected {
        background-color: $tabbar-tab-item-selected-background-color;
        color: $tabbar-tab-item-selected-color;
      }
    }
  }
</style>
