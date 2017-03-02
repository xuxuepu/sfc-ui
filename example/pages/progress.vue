<template>
  <div class="page-progress">
    <h1 class="page-title">Progress</h1>
    <sfc-cell title="默认">
      <sfc-progress></sfc-progress>
    </sfc-cell>
    <sfc-cell title="设置 value">
      <sfc-progress :value="20"></sfc-progress>
    </sfc-cell>
    <sfc-cell title="左右文字">
      <sfc-progress :value="40">
        <div slot="start">0%</div>
        <div slot="end">100%</div>
      </sfc-progress>
    </sfc-cell>
    <sfc-cell title="定义线宽">
      <sfc-progress :value="60" :bar-height="5"></sfc-progress>
    </sfc-cell>
    <div class="page-progress-wrapper">
      <sfc-button size="large" type="primary" @click.native="uploadFile">上传文件</sfc-button>
      <sfc-progress :value="value" v-if="progressVisible" transition="progress-fade">
        <div slot="end">{{ value }}%</div>
      </sfc-progress>
    </div>
  </div>
</template>

<style>
  @component-namespace page {
    @component progress {
      .sfc-cell-value {
        flex: 2.5;
        position: relative;
        top: -20px;
      }

      .sfc-progress {
        width: 100%;
        position: absolute;
        top: 5px;
      }

      @descendent wrapper {
        padding: 0 10px;
        margin-top: 50px;

        .sfc-progress {
          position: relative;
        }

        .progress-fade-transition {
          transition: opacity .3s;
        }

        .progress-fade-enter,
        .progress-fade-leave {
          opacity: 0;
        }
      }
    }
  }
</style>

<script type="text/babel">
  import { Toast } from 'src/index';

  export default {
    data() {
      return {
        progressVisible: false,
        value: 0,
        uploading: false,
        timer: null
      };
    },

    watch: {
      value(val) {
        if (val >= 100) {
          this.uploading = false;
          this.progressVisible = false;
          setTimeout(() => Toast({ message: '上传成功', position: 'bottom', duration: 1000 }), 200);
          clearTimeout(this.timer);
        }
      }
    },

    methods: {
      uploadFile() {
        if (!this.uploading) {
          this.value = 0;
          this.progressVisible = true;
          this.uploading = true;
          this.timer = setInterval(() => this.value++, 10);
        }
      }
    }
  };
</script>