<template>
  <a class="sfc-tab-item"
    @click="$parent.$emit('input', id)"
    :class="{ 'is-selected': $parent.value === id }">
    <div class="sfc-tab-item-icon"><slot name="icon"></slot></div>
    <div class="sfc-tab-item-label"><slot></slot></div>
  </a>
</template>

<script>
/**
 * sfc-tab-item
 * @module components/tab-item
 * @desc 搭配 tabbar 或 navbar 使用
 * @param {*} id - 选中后的返回值，任意类型
 * @param {slot} [icon] - icon 图标
 * @param {slot} - 文字
 *
 * @example
 * <sfc-tab-item>
 *   <img slot="icon" src="http://placehold.it/100x100">
 *   订单
 * </sfc-tab-item>
 */
export default {
  name: 'sfc-tab-item',

  props: ['id']
};
</script>

<style lang="css">
  @import "../../../src/style/var.css";

  @component-namespace sfc {
    @component tab-item {
      display: block;
      padding: 7px 0;
      flex: 1;
      text-decoration: none;

      @descendent icon {
        size: 24px;
        margin: 0 auto 5px;

        &:empty {
          display: none;
        }

        & > * {
          display: block;
          size: 100%;
        }
      }

      @descendent label {
        color: inherit;
        font-size: $tab-item-font-size;
        line-height: 1;
      }
    }
  }
</style>
