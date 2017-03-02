<template>
  <div class="sfc-radiolist" @change="$emit('change', currentValue)">
    <label class="sfc-radiolist-title" v-text="title"></label>
    <x-cell v-for="option in options">
      <label class="sfc-radiolist-label" slot="title">
        <span
          :class="{'is-right': align === 'right'}"
          class="sfc-radio">
          <input
            class="sfc-radio-input"
            type="radio"
            v-model="currentValue"
            :disabled="option.disabled"
            :value="option.value || option">
          <span class="sfc-radio-core"></span>
        </span>
        <span class="sfc-radio-label" v-text="option.label || option"></span>
      </label>
    </x-cell>
  </div>
</template>

<script>
import XCell from 'sfc-ui/packages/cell/index.js';
if (process.env.NODE_ENV === 'component') {
  require('sfc-ui/packages/cell/style.css');
}
/**
 * sfc-radio
 * @module components/radio
 * @desc 单选框列表，依赖 cell 组件
 *
 * @param {string[], object[]} options - 选项数组，可以传入 [{label: 'label', value: 'value', disabled: true}] 或者 ['ab', 'cd', 'ef']
 * @param {string} value - 选中值
 * @param {string} title - 标题
 * @param {string} [align=left] - checkbox 对齐位置，`left`, `right`
 *
 * @example
 * <sfc-radio v-model="value" :options="['a', 'b', 'c']"></sfc-radio>
 */
export default {
  name: 'sfc-radio',

  props: {
    title: String,
    align: String,
    options: {
      type: Array,
      required: true
    },
    value: String
  },

  data() {
    return {
      currentValue: this.value
    };
  },

  watch: {
    value(val) {
      this.currentValue = val;
    },

    currentValue(val) {
      this.$emit('input', val);
    }
  },

  components: {
    XCell
  }
};
</script>

<style lang="css">
  @import "../../../src/style/var.css";

  @component-namespace sfc {
    @component radiolist {

      .sfc-cell {
        padding: 0;
      }

      @descendent label {
        display: block;
        padding: 0 10px;
      }

      @descendent title {
        font-size: 12px;
        margin: 8px;
        display: block;
        color: $radio-title-color;
      }
    }

    @component radio {
      @when right {
        float: right;
      }

      @descendent label {
        vertical-align: middle;
        margin-left: 6px;
      }

      @descendent input {
        display: none;

        &:checked {
          + .sfc-radio-core {
            background-color: $color-primary;
            border-color: $color-primary;

            &::after {
              background-color: $color-white;
              transform: scale(1);
            }
          }
        }

        &[disabled] + .sfc-radio-core {
          background-color: $color-grey;
          border-color: #ccc;
        }
      }

      @descendent core {
        display: inline-block;
        background-color: $color-white;
        border-radius: 100%;
        border: 1px solid #ccc;
        position: relative;
        size: 20px;
        vertical-align: middle;

        &::after {
          content: " ";
          border-radius: 100%;
          position: absolute 5px * * 5px;
          size: 8px;
          transition: transform .2s;
          transform: scale(0);
        }
      }
    }
  }
</style>
