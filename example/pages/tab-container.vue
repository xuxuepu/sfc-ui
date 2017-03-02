<template>
  <div>
    <div class="nav">
      <sfc-button size="small" @click.native.prevent="active = 'tab-container1'">tab 1</sfc-button>
      <sfc-button size="small" @click.native.prevent="active = 'tab-container2'">tab 2</sfc-button>
      <sfc-button size="small" @click.native.prevent="active = 'tab-container3'">tab 3</sfc-button>
    </div>
    <div class="page-tab-container">
      <sfc-tab-container class="page-tabbar-tab-container" v-model="active" swipeable>
        <sfc-tab-container-item id="tab-container1">
          <sfc-cell v-for="n in 10" title="tab-container 1"></sfc-cell>
        </sfc-tab-container-item>
        <sfc-tab-container-item id="tab-container2">
          <sfc-cell v-for="n in 5" title="tab-container 2"></sfc-cell>
        </sfc-tab-container-item>
        <sfc-tab-container-item id="tab-container3">
          <sfc-cell v-for="n in 7" title="tab-container 3"></sfc-cell>
        </sfc-tab-container-item>
      </sfc-tab-container>
    </div>
  </div>
</template>

<script>
export default {
  name: 'page-tab-container',
  data() {
    return {
      active: 'tab-container1'
    };
  }
};
</script>

<style lang="css" scoped>
  .item {
    display: inline-block;
  }

  .nav {
    padding: 10px;
  }

  .link {
    color: inherit;
    padding: 20px;
    display: block;
  }
</style>
