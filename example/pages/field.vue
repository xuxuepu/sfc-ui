<template>
  <div class="page-field">
    <div class="page-title">Field</div>
    <div class="page-part">
      <sfc-field label="用户名" placeholder="请输入用户名" :attr="{ maxlength: 10 }"></sfc-field>
      <sfc-field label="邮箱" placeholder="请输入邮箱" type="email"></sfc-field>
      <sfc-field label="密码" placeholder="请输入密码" type="password"></sfc-field>
      <sfc-field label="手机号" placeholder="请输入手机号" type="tel"></sfc-field>
      <sfc-field label="网站" placeholder="请输入网址" type="url"></sfc-field>
      <sfc-field label="数字" placeholder="请输入数字" type="number"></sfc-field>
      <sfc-field label="生日" placeholder="请输入生日" type="date"></sfc-field>
      <sfc-field label="自我介绍" placeholder="自我介绍" type="textarea" rows="4"></sfc-field>
    </div>

    <div class="page-part">
      <sfc-field placeholder="登录邮箱" type="email"></sfc-field>
      <sfc-field placeholder="密码" type="password"></sfc-field>
    </div>

    <div class="page-part">
      <sfc-field label="邮箱" placeholder="成功状态" state="success"></sfc-field>
      <sfc-field label="邮箱" placeholder="失败状态" state="error"></sfc-field>
      <sfc-field label="邮箱" placeholder="警告状态" state="warning"></sfc-field>
    </div>

    <div class="page-part">
      <sfc-field label="验证码" placeholder="输入验证码">
        <img src="../assets/100x100.png" height="48px" width="100px">
      </sfc-field>
    </div>
  </div>
</template>

<script>
export default {
  name: 'page-field'
};
</script>
