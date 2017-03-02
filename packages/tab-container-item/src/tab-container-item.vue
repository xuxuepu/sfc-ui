<template>
  <div
    v-show="$parent.swiping || id === $parent.currentActive"
    class="sfc-tab-container-item">
    <slot></slot>
  </div>
</template>

<script>
/**
 * sfc-tab-container-item
 * @desc 搭配 tab-container 使用
 * @module components/tab-container-item
 *
 * @param {number|string} [id] - 该项的 id
 *
 * @example
 * <sfc-tab-container v-model="selected">
 *   <sfc-tab-container-item id="1"> 内容A </sfc-tab-container-item>
 *   <sfc-tab-container-item id="2"> 内容B </sfc-tab-container-item>
 *   <sfc-tab-container-item id="3"> 内容C </sfc-tab-container-item>
 * </sfc-tab-container>
 */
export default {
  name: 'sfc-tab-container-item',

  props: ['id']
};
</script>

<style>
  @component-namespace sfc {
    @component tab-container-item {
      flex-shrink: 0;
      width: 100%;
    }
  }
</style>
