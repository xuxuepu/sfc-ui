<template>
  <div class="page-navbar">
    <div class="page-title">Navbar</div>
    <sfc-navbar class="page-part" v-model="selected">
      <sfc-tab-item id="1">选项一</sfc-tab-item>
      <sfc-tab-item id="2">选项二</sfc-tab-item>
      <sfc-tab-item id="3">选项三</sfc-tab-item>
    </sfc-navbar>

    <div>
      <sfc-cell class="page-part" title="当前选中">{{ selected }}</sfc-cell>
    </div>

    <sfc-tab-container v-model="selected">
      <sfc-tab-container-item id="1">
        <sfc-cell v-for="n in 10" :title="'内容 ' + n" />
      </sfc-tab-container-item>
      <sfc-tab-container-item id="2">
        <sfc-cell v-for="n in 4" :title="'测试 ' + n" />
      </sfc-tab-container-item>
      <sfc-tab-container-item id="3">
        <sfc-cell v-for="n in 6" :title="'选项 ' + n" />
      </sfc-tab-container-item>
    </sfc-tab-container>
  </div>
</template>

<script>
export default {
  name: 'page-navbar',

  data() {
    return {
      selected: '1'
    };
  }
};
</script>
