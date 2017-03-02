<template>
  <div class="page-tabbar">
    <div class="page-wrap">
      <div class="page-title">Tabbar</div>
      <div>
        <sfc-cell class="page-part" title="当前选中" :value="selected" />
      </div>

      <sfc-tab-container class="page-tabbar-container" v-model="selected">
        <sfc-tab-container-item id="外卖">
          <sfc-cell v-for="n in 10" :title="'餐厅 ' + n" />
        </sfc-tab-container-item>
        <sfc-tab-container-item id="订单">
          <sfc-cell v-for="n in 5" :title="'订单 ' + n" />
        </sfc-tab-container-item>
        <sfc-tab-container-item id="发现">
          <sfc-cell v-for="n in 7" :title="'发现 ' + n" />
        </sfc-tab-container-item>
        <sfc-tab-container-item id="我的">
          <div class="page-part">
            <sfc-cell v-for="n in 12" :title="'我的 ' + n" />
          </div>
          <router-link to="/">
            <sfc-button type="danger" size="large">退出</sfc-button>
          </router-link>
        </sfc-tab-container-item>
      </sfc-tab-container>
    </div>

    <sfc-tabbar v-model="selected" fixed>
      <sfc-tab-item id="外卖">
        <img slot="icon" src="../assets/100x100.png">
        外卖
      </sfc-tab-item>
      <sfc-tab-item id="订单">
        <img slot="icon" src="../assets/100x100.png">
        订单
      </sfc-tab-item>
      <sfc-tab-item id="发现">
        <img slot="icon" src="../assets/100x100.png">
        发现
      </sfc-tab-item>
      <sfc-tab-item id="我的">
        <img slot="icon" src="../assets/100x100.png">
        我的
      </sfc-tab-item>
    </sfc-tabbar>
  </div>
</template>

<script>
export default {
  name: 'page-tabbar',
  data() {
    return {
      selected: '外卖'
    };
  }
};
</script>

<style>
  .page-tabbar {
    overflow: hidden;
    height: 100vh;
  }

  .page-wrap {
    overflow: auto;
    height: 100%;
    padding-bottom: 100px;
  }
</style>
