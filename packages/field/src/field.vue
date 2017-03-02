<template>
  <x-cell
    class="sfc-field"
    :title="label"
    v-clickoutside="doCloseActive"
    :class="[{
      'is-textarea': type === 'textarea',
      'is-nolabel': !label
    }]">
    <textarea
      @change="$emit('change', currentValue)"
      ref="textarea"
      class="sfc-field-core"
      :placeholder="placeholder"
      v-if="type === 'textarea'"
      :rows="rows"
      :disabled="disabled"
      :readonly="readonly"
      v-model="currentValue">
    </textarea>
    <input
      @change="$emit('change', currentValue)"
      ref="input"
      class="sfc-field-core"
      :placeholder="placeholder"
      :number="type === 'number'"
      v-else
      :type="type"
      @focus="active = true"
      :disabled="disabled"
      :readonly="readonly"
      :value="currentValue"
      @input="handleInput">
    <div
      @click="handleClear"
      class="sfc-field-clear"
      v-if="!disableClear"
      v-show="currentValue && type !== 'textarea' && active">
      <i class="sfcui sfcui-field-error"></i>
    </div>
    <span class="sfc-field-state" v-if="state" :class="['is-' + state]">
      <i class="sfcui" :class="['sfcui-field-' + state]"></i>
    </span>
    <div class="sfc-field-other">
      <slot></slot>
    </div>
  </x-cell>
</template>

<script>
import XCell from 'sfc-ui/packages/cell/index.js';
import Clickoutside from 'sfc-ui/src/utils/clickoutside';
if (process.env.NODE_ENV === 'component') {
  require('sfc-ui/packages/cell/style.css');
}

/**
 * sfc-field
 * @desc 编辑器，依赖 cell
 * @module components/field
 *
 * @param {string} [type=text] - field 类型，接受 text, textarea 等
 * @param {string} [label] - 标签
 * @param {string} [rows] - textarea 的 rows
 * @param {string} [placeholder] - placeholder
 * @param {string} [disabled] - disabled
 * @param {string} [readonly] - readonly
 * @param {string} [state] - 表单校验状态样式，接受 error, warning, success
 *
 * @example
 * <sfc-field v-model="value" label="用户名"></sfc-field>
 * <sfc-field v-model="value" label="密码" placeholder="请输入密码"></sfc-field>
 * <sfc-field v-model="value" label="自我介绍" placeholder="自我介绍" type="textarea" rows="4"></sfc-field>
 * <sfc-field v-model="value" label="邮箱" placeholder="成功状态" state="success"></sfc-field>
 */
export default {
  name: 'sfc-field',

  data() {
    return {
      active: false,
      currentValue: this.value
    };
  },

  directives: {
    Clickoutside
  },

  props: {
    type: {
      type: String,
      default: 'text'
    },
    rows: String,
    label: String,
    placeholder: String,
    readonly: Boolean,
    disabled: Boolean,
    disableClear: Boolean,
    state: {
      type: String,
      default: 'default'
    },
    value: {},
    attr: Object
  },

  components: { XCell },

  methods: {
    doCloseActive() {
      this.active = false;
    },

    handleInput(evt) {
      this.currentValue = evt.target.value;
    },

    handleClear() {
      if (this.disabled || this.readonly) return;
      this.currentValue = '';
    }
  },

  watch: {
    value(val) {
      this.currentValue = val;
    },

    currentValue(val) {
      this.$emit('input', val);
    },

    attr: {
      immediate: true,
      handler(attrs) {
        this.$nextTick(() => {
          const target = [this.$refs.input, this.$refs.textarea];
          target.forEach(el => {
            if (!el || !attrs) return;
            Object.keys(attrs).map(name => el.setAttribute(name, attrs[name]));
          });
        });
      }
    }
  }
};
</script>

<style lang="css">
  @import "../../../src/style/var.css";

  @component-namespace sfc {
    @component field {
      display: flex;

      @when textarea {
        align-items: inherit;

        .sfc-cell-title {
          padding: 10px 0;
        }

        .sfc-cell-value {
          padding: 5px 0;
        }
      }

      .sfc-cell-title {
        width: 105px;
        flex: none;
      }

      .sfc-cell-value {
        flex: 1;
        color: inherit;
        display: flex;
      }

      @descendent core {
        appearance: none;
        border-radius: 0;
        border: 0;
        flex: 1;
        outline: 0;
        line-height: 1.6;
        font-size: inherit;
        width: 100%;
      }

      @descendent clear {
        opacity: .2;
      }

      @descendent state {
        color: inherit;
        margin-left: 20px;

        .sfcui {
          font-size: 20px;
        }

        @when error {
          color: $error-color;
        }

        @when warning {
          color: $warning-color;
        }

        @when success {
          color: $success-color;
        }

        @when default {
          margin-left: 0;
        }
      }

      @descendent other {
        position: absolute 0 0 * *;
      }

      @when nolabel {
        .sfc-cell-title {
          display: none;
        }
      }
    }
  }
</style>
