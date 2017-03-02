<template>
  <div>
    <sfc-header fixed title="固定在顶部"></sfc-header>
    <div class="page-header-main">
      <div class="page-title">Header</div>
      <sfc-header title="标题过长会隐藏后面的内容啊哈哈哈哈">
        <router-link to="/" slot="left">
          <sfc-button icon="back">返回</sfc-button>
        </router-link>
        <sfc-button icon="more" slot="right"></sfc-button>
      </sfc-header>

      <sfc-header title="多个按钮">
        <router-link to="/" slot="left">
          <sfc-button icon="back">返回</sfc-button>
        </router-link>
        <sfc-button @click="handleClose">关闭</sfc-button>
        <sfc-button icon="more" slot="right"></sfc-button>
      </sfc-header>

      <sfc-header title="左侧仅文字">
        <router-link to="/" slot="left">
            <sfc-button>返回</sfc-button>
          </router-link>
      </sfc-header>

      <sfc-header title="右侧仅文字">
        <router-link to="/" slot="right">
          <sfc-button>分享</sfc-button>
        </router-link>
      </sfc-header>

      <sfc-header title="仅图标">
        <router-link to="/" slot="left">
          <sfc-button icon="back"></sfc-button>
        </router-link>
        <sfc-button slot="right" icon="more"></sfc-button>
      </sfc-header>
    </div>

  </div>
</template>

<script>
export default {
  name: 'header',

  data() {
    return {

    };
  },

  methods: {
    handleClose() {
      alert('close this page');
    }
  }
};
</script>

<style lang="css">
  @component-namespace page {
    @component header {
      @descendent main {
        margin-top: 50px;
        min-height: 120vh;

        > * {
          margin-bottom: 15px;
        }
      }
    }
  }
</style>
