<template>
  <div class="sfc-search">
    <div class="sfc-searchbar">
      <div class="sfc-searchbar-inner">
        <i class="sfcui sfcui-search" v-show="visible"></i>
        <input
        ref="input"
        @click="visible = true"
        type="search"
        v-model="currentValue"
        :placeholder="visible ? placeholder : ''"
        class="sfc-searchbar-core">
      </div>
      <a
        class="sfc-searchbar-cancel"
        @click="visible = false, currentValue = ''"
        v-show="visible"
        v-text="cancelText">
      </a>
      <label
        @click="visible = true, $refs.input.focus()"
        class="sfc-searchbar-placeholder"
        v-show="!visible">
        <i class="sfcui sfcui-search"></i>
        <span class="sfc-searchbar-text" v-text="placeholder"></span>
      </label>
    </div>
    <div class="sfc-search-list" v-show="show || currentValue">
      <div class="sfc-search-list-warp">
        <slot>
          <x-cell v-for="(item, index) in result" :key="index" :title="item"></x-cell>
        </slot>
      </div>
    </div>
  </div>
</template>

<script>
import XCell from 'sfc-ui/packages/cell/index.js';
if (process.env.NODE_ENV === 'component') {
  require('sfc-ui/packages/cell/style.css');
}

/**
 * sfc-search
 * @module components/search
 * @desc 搜索框
 * @param {string} value - 绑定值
 * @param {string} [cancel-text=取消] - 取消按钮文字
 * @param {string} [placeholder=取消] - 搜索框占位内容
 * @param {boolean} [autofocus=false] - 自动 focus
 * @param {boolean} [show=false] - 始终显示列表
 * @param {string[]} [result] - 结果列表
 * @param {slot} 结果列表
 *
 * @example
 * <sfc-search :value.sync="value" :result.sync="result"></sfc-search>
 * <sfc-search :value.sync="value">
 *   <sfc-cell v-for="item in result" :title="item"></sfc-cell>
 * </sfc-search>
 */
export default {
  name: 'sfc-search',

  data() {
    return {
      visible: false,
      currentValue: this.value
    };
  },

  components: { XCell },

  watch: {
    currentValue(val) {
      this.$emit('input', val);
    },

    value(val) {
      this.currentValue = val;
    }
  },

  props: {
    value: String,
    autofocus: Boolean,
    show: Boolean,
    cancelText: {
      default: '取消'
    },
    placeholder: {
      default: '搜索'
    },
    result: Array
  },

  mounted() {
    this.autofocus && this.$refs.input.focus();
  }
};
</script>

<style lang="css">
  @import "../../../src/style/var.css";

  @component-namespace sfc {
    @component search {
      height: 100%;
      height: 100vh;
      overflow: hidden;
    }

    @component searchbar {
      position: relative;
      align-items: center;
      background-color: $color-grey;
      box-sizing: border-box;
      display: flex;
      padding: 8px 10px;
      z-index: 1;

      @descendent inner {
        align-items: center;
        background-color: $color-white;
        border-radius: 2px;
        display: flex;
        flex: 1;
        height: 28px;
        padding: 4px 6px;

        .sfcui-search {
          font-size: 12px;
          color: $color-grey;
        }
      }

      @descendent core {
        appearance: none;
        border: 0;
        box-sizing: border-box;
        height: 100%;
        outline: 0;
      }

      @descendent placeholder {
        align-items: center;
        color: #9b9b9b;
        display: flex;
        font-size: 12px;
        justify-content: center;
        position: absolute 0 0 0 0;

        .sfcui-search {
          font-size: 12px;
        }
      }

      @descendent cancel {
        color: $color-primary;
        margin-left: 10px;
        text-decoration: none;
      }
    }

    @component search-list {
      overflow: auto;
      padding-top: 44px;
      position: absolute 0 0 0 0;
    }
  }
</style>
