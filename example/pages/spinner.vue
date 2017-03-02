<template>
  <div class="page-spinner">
    <div class="page-title">Spinner</div>

    <sfc-cell title="snake">
      <sfc-spinner color="#26a2ff" type="snake"></sfc-spinner>
    </sfc-cell>

    <sfc-cell title="double-bounce">
      <sfc-spinner color="#26a2ff" type="double-bounce"></sfc-spinner>
    </sfc-cell>

    <sfc-cell title="triple-bounce">
      <sfc-spinner color="#26a2ff" type="triple-bounce"></sfc-spinner>
    </sfc-cell>

    <sfc-cell title="fading-circle">
      <sfc-spinner color="#26a2ff" type="fading-circle"></sfc-spinner>
    </sfc-cell>
  </div>
</template>

<script>
export default {
  name: 'page-spinner',

  data() {
    return {

    };
  }
};
</script>

<style lang="css">
  @component-namespace page {
    @component spinner {
      .sfc-cell {
        min-height: 50px;
      }
    }
  }
</style>