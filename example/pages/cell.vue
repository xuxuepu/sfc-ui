<template>
  <div class="page-cell">
    <div class="page-title">Cell</div>
    <sfc-cell title="标题文字"></sfc-cell>
    <sfc-cell title="标题文字" value="说明文字"></sfc-cell>
    <sfc-cell title="标题文字" icon="more" value="带 icon"></sfc-cell>
    <sfc-cell title="标题文字" icon="more">
      <span>icon 是图片</span>
      <img slot="icon" src="../assets/100x100.png" width="24" height="24">
    </sfc-cell>
    <sfc-cell title="标题文字" is-link value="带链接"></sfc-cell>
    <sfc-cell title="标题文字" is-link>
      <span style="color: green">这里是元素</span>
    </sfc-cell>
    <sfc-cell title="标题文字">
      <sfc-button size="small" type="primary" icon="back">按钮</sfc-button>
    </sfc-cell>

    <sfc-cell title="标题" label="描述信息" is-link></sfc-cell>

    <sfc-cell title="原生跳转" label="跳转到 https://sfc-ui.github.io" is-link to="https://sfc-ui.github.io"></sfc-cell>
    <sfc-cell title="路由跳转" label="跳转到 /#/toast" is-link :to="{ name: 'Toast' }"></sfc-cell>
  </div>
</template>
