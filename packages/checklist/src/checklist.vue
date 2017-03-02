<template>
  <div @change="$emit('change', currentValue)" class="sfc-checklist" :class="{ 'is-limit': max <= currentValue.length }">
    <label class="sfc-checklist-title" v-text="title"></label>
    <x-cell v-for="option in options">
      <label class="sfc-checklist-label" slot="title">
        <span
          :class="{'is-right': align === 'right'}"
          class="sfc-checkbox">
          <input
            class="sfc-checkbox-input"
            type="checkbox"
            v-model="currentValue"
            :disabled="option.disabled"
            :value="option.value || option">
          <span class="sfc-checkbox-core"></span>
        </span>
        <span class="sfc-checkbox-label" v-text="option.label || option"></span>
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
 * sfc-checklist
 * @module components/checklist
 * @desc 复选框列表，依赖 cell 组件
 *
 * @param {(string[]|object[])} options - 选项数组，可以传入 [{label: 'label', value: 'value', disabled: true}] 或者 ['ab', 'cd', 'ef']
 * @param {string[]} value - 选中值的数组
 * @param {string} title - 标题
 * @param {number} [max] - 最多可选的个数
 * @param {string} [align=left] - checkbox 对齐位置，`left`, `right`
 *
 *
 * @example
 * <sfc-checklist :v-model="value" :options="['a', 'b', 'c']"></sfc-checklist>
 */
export default {
  name: 'sfc-checklist',

  props: {
    max: Number,
    title: String,
    align: String,
    options: {
      type: Array,
      required: true
    },
    value: Array
  },

  components: { XCell },

  data() {
    return {
      currentValue: this.value
    };
  },

  computed: {
    limit() {
      return this.max < this.currentValue.length;
    }
  },

  watch: {
    value(val) {
      this.currentValue = val;
    },

    currentValue(val) {
      if (this.limit) val.pop();
      this.$emit('input', val);
    }
  }
};
</script>

<style lang="css">
  @import "../../../src/style/var.css";

  @component-namespace sfc {
    @component checklist {

      .sfc-cell {
        padding: 0;
      }

      @descendent label {
        display: block;
        padding: 0 10px;
      }

      @descendent title {
        color: $checklist-title-color;
        display: block;
        font-size: 12px;
        margin: 8px;
      }

      @when limit {
        .sfc-checkbox-core:not(:checked) {
          background-color: $color-grey;
          border-color: $color-grey;
        }
      }
    }

    @component checkbox {
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
          + .sfc-checkbox-core {
            background-color: $color-primary;
            border-color: $color-primary;

            &::after {
              border-color: $color-white;
              transform: rotate(45deg) scale(1);
            }
          }
        }

        &[disabled] + .sfc-checkbox-core {
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
          border: 2px solid transparent;
          border-left: 0;
          border-top: 0;
          content: " ";
          position: absolute 3px * * 6px;
          size: 4px 8px;
          transform: rotate(45deg) scale(0);
          transition: transform .2s;
        }
      }
    }
  }
</style>
