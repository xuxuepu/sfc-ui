<template>
  <div class="page-switch">
    <div class="page-title">Switch</div>
    <div class="page-part page-switch-padding">
      <sfc-switch v-model="value1" @change="handleChange">
        <label v-text="value1"></label>
      </sfc-switch>
    </div>

    <div class="page-part page-switch-padding">
      <sfc-switch v-model="value4" @change="handleChange">
        <label v-text="value4"></label>
      </sfc-switch>
    </div>

    <sfc-cell :title="'选项 ' + value2">
      <sfc-switch v-model="value2" @change="handleChange"></sfc-switch>
    </sfc-cell>
    <sfc-cell :title="'选项 ' + value3">
      <sfc-switch v-model="value3" @change="handleChange"></sfc-switch>
    </sfc-cell>
  </div>
</template>

<script>
export default {
  name: 'page-switch',

  data() {
    return {
      value1: false,
      value2: false,
      value3: true,
      value4: true
    };
  },

  methods: {
    handleChange(event) {
      console.log(event);
    }
  }
};
</script>

<style lang="css">
  @component-namespace page {
    @component switch {
      @descendent padding {
        padding: 0 10px;
      }
    }
  }
</style>
