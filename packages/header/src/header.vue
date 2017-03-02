<template>
  <header
    class="sfc-header"
    :class="{ 'is-fixed': fixed }">
    <div class="sfc-header-button is-left">
      <slot name="left"></slot>
    </div>
    <h1 class="sfc-header-title" v-text="title"></h1>
    <div class="sfc-header-button is-right">
      <slot name="right"></slot>
    </div>
  </header>
</template>

<script>
/**
 * sfc-header
 * @module components/header
 * @desc 顶部导航
 * @param {boolean} [fixed=false] - 固定顶部
 * @param {string} [title] - 标题
 * @param {slot} [left] - 显示在左侧区域
 * @param {slot} [right] - 显示在右侧区域
 *
 * @example
 * <sfc-header title="我是标题" fixed>
 *   <sfc-button slot="left" icon="back" @click="handleBack">返回</sfc-button>
 *   <sfc-button slot="right" icon="more"></sfc-button>
 * </sfc-header>
 */
export default {
  name: 'sfc-header',

  props: {
    fixed: Boolean,
    title: String
  }
};
</script>

<style lang="css">
  @import "../../../src/style/var.css";

  @component-namespace sfc {
    @component header {
      align-items: center;
      background-color: $color-primary;
      box-sizing: border-box;
      color: $color-white;
      display: flex;
      font-size: 14px;
      height: $header-height;
      line-height: 1;
      padding: 0 10px;
      position: relative;
      text-align: center;
      white-space: nowrap;

      .sfc-button {
        background-color: transparent;
        border: 0;
        box-shadow: none;
        color: inherit;
        display: inline-block;
        padding: 0;
        font-size: inherit;

        &::after {
          content: none;
        }
      }

      @descendent button {
        flex: .5;

        > a {
          color: inherit;
        }

        @when left {
          text-align: left;
        }

        @when right {
          text-align: right;
        }
      }

      @descendent title {
        @utils-ellipsis;
        font-size: inherit;
        font-weight: normal;
        flex: 1;
      }

      @when fixed {
        position: fixed 0 0 * 0;
        z-index: $z-index-normal;
      }
    }
  }
</style>
