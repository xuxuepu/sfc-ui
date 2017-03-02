<template>
  <div class="page-swipe">
    <h1 class="page-title">Swipe</h1>
    <p class="page-swipe-desc">基础用法</p>
    <sfc-swipe :auto="4000">
      <sfc-swipe-item class="slide1">1</sfc-swipe-item>
      <sfc-swipe-item class="slide2">2</sfc-swipe-item>
      <sfc-swipe-item class="slide3">3</sfc-swipe-item>
    </sfc-swipe>

    <p class="page-swipe-desc">隐藏 indicators</p>
    <sfc-swipe :show-indicators="false">
      <sfc-swipe-item class="slide1">1</sfc-swipe-item>
      <sfc-swipe-item class="slide2">2</sfc-swipe-item>
      <sfc-swipe-item class="slide3">3</sfc-swipe-item>
    </sfc-swipe>

    <p class="page-swipe-desc">取消自动播放</p>
    <sfc-swipe :auto="0">
      <sfc-swipe-item class="slide1">1</sfc-swipe-item>
      <sfc-swipe-item class="slide2">2</sfc-swipe-item>
      <sfc-swipe-item class="slide3">3</sfc-swipe-item>
    </sfc-swipe>

    <p class="page-swipe-desc">设置默认显示页</p>
    <sfc-swipe :auto="0" :defaultIndex="1">
      <sfc-swipe-item class="slide1">1</sfc-swipe-item>
      <sfc-swipe-item class="slide2">2</sfc-swipe-item>
      <sfc-swipe-item class="slide3">3</sfc-swipe-item>
    </sfc-swipe>

    <p class="page-swipe-desc">单个幻灯片</p>
    <sfc-swipe :show-indicators="false">
      <sfc-swipe-item class="slide1">SINGLE SLIDE</sfc-swipe-item>
    </sfc-swipe>
  </div>
</template>

<style>
  @component-namespace page {
    @component swipe {
      @descendent desc {
        text-align: center;
        color: #666;
        margin-bottom: 5px;
      }
      .sfc-swipe {
        height: 200px;
        color: #fff;
        font-size: 30px;
        text-align: center;
        margin-bottom: 20px;
      }

      .sfc-swipe-item {
        line-height: 200px;
      }

      .slide1 {
        background-color: #0089dc;
        color: #fff;
      }

      .slide2 {
        background-color: #ffd705;
        color: #000;
      }

      .slide3 {
        background-color: #ff2d4b;
        color: #fff;
      }
    }
  }
</style>
