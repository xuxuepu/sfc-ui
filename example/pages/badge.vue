<template>
  <div class="page-badge">
    <div class="page-title">Badge</div>

    <div class="page-badge-container">
      <div class="page-part">
        <sfc-badge type="primary" size="large">30</sfc-badge>
        <sfc-badge type="error" size="large">10</sfc-badge>
        <sfc-badge type="success" size="large">10</sfc-badge>
        <sfc-badge type="warning" size="large">10</sfc-badge>
      </div>

      <div class="page-part">
        <sfc-badge type="primary">30</sfc-badge>
        <sfc-badge type="error">10</sfc-badge>
        <sfc-badge type="success">10</sfc-badge>
        <sfc-badge type="warning">10</sfc-badge>
      </div>

      <div class="page-part">
        <sfc-badge type="primary" size="small">30</sfc-badge>
        <sfc-badge type="error" size="small">10</sfc-badge>
        <sfc-badge type="success" size="small">10</sfc-badge>
        <sfc-badge type="warning" size="small">10</sfc-badge>
      </div>

      <div class="page-part">
        <sfc-badge size="small" color="#888">自定义颜色</sfc-badge>
      </div>
    </div>

    <div class="page-part">
      <sfc-cell title="徽章">
        <span style="margin-right: 5px;">未读消息</span>
        <sfc-badge type="error" size="small">10</sfc-badge>
      </sfc-cell>
    </div>
  </div>
</template>

<script>
export default {
  name: 'page-badge'
};
</script>

<style lang="css">
  .page-badge-container {
    padding: 0 10px;
  }
</style>
