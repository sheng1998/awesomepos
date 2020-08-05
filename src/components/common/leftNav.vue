<template>
  <div class="leftNav">
    <ul>
      <li>
        <i class="iconfont icon-goumai"></i>
        <div>收银</div>
      </li>
      <li>
        <i class="iconfont icon-jinrudianpu"></i>
        <div>店铺</div>
      </li>
      <li>
        <i class="iconfont icon-hanbao"></i>
        <div>商品</div>
      </li>
      <li>
        <i class="iconfont icon-huiyuanqia"></i>
        <div>会员</div>
      </li>
      <li>
        <i class="iconfont icon-tongji"></i>
        <div>统计</div>
      </li>
      <li>
        <i class="iconfont icon-shezhi"></i>
        <div>设置</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {}
</script>

<style lang="less" scoped>
.leftNav {
  float: left;
  height: 100%;
  width: 5%;
  overflow: hidden;
  color: #fff;
  background-color: #1D8CE0;
  font-size: 12px;

  ul {
    padding: 0;
    margin: 0;

    li {
      list-style: none;
      text-align: center;
      border-bottom: 1px solid #20a0ff;
      padding: 10px;

      .iconfont {
        font-size: 24px;
      }

      div {
        margin-top: 5px;
      }
    }
  }
}
</style>
