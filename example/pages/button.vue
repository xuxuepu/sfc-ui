<template>
  <div class="page-button">
    <h1 class="page-title">Button</h1>
    <div class="page-button-group">
      <sfc-button size="large">default</sfc-button>
      <sfc-button size="large" type="primary">primary</sfc-button>
      <sfc-button size="large" type="danger">danger</sfc-button>
    </div>

    <div class="page-button-group">
      <sfc-button>default</sfc-button>
      <sfc-button type="primary">primary</sfc-button>
      <sfc-button type="danger">danger</sfc-button>
    </div>

    <div class="page-button-group">
      <sfc-button size="small">default</sfc-button>
      <sfc-button size="small" type="primary">primary</sfc-button>
      <sfc-button size="small" type="danger">danger</sfc-button>
    </div>

    <div class="page-button-group">
      <sfc-button disabled size="large">default</sfc-button>
      <sfc-button disabled size="large" type="primary">primary</sfc-button>
      <sfc-button disabled size="large" type="danger">danger</sfc-button>
    </div>

    <div class="page-button-group">
      <sfc-button plain size="large">default</sfc-button>
      <sfc-button plain size="large" type="primary">primary</sfc-button>
      <sfc-button plain size="large" type="danger">danger</sfc-button>
    </div>

    <div class="page-button-group">
      <sfc-button>
        <img src="../assets/100x100.png" height="20" width="20" slot="icon">
        带自定义图标
      </sfc-button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'button'
};
</script>

<style lang="css">
  @component-namespace page {
    @component button {
      padding: 0 15px 15px;

      @descendent group {
        margin-bottom: 15px;

        & > * {
          margin-bottom: 15px;
        }
      }
    }
  }
</style>
