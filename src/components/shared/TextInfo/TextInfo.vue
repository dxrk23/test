<template>
  <div class="text">
    <div class="text-title">
      <span><slot name="title"></slot></span>
    </div>
    <div class="text-content">
      <span><slot name="content"></slot></span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TextInfo"
}
</script>

<style lang="scss">
.text {
  font-family: 'Average Sans', sans-serif;
  font-style: normal;
  color: #1E1E1E;
  font-weight: 400;

  padding: 45px 45px 35px 35px;

  &-title {
    font-size: 30px;
    line-height: 39px;
  }
  &-content {
    margin-top: 48px;

    font-size: 20px;
    line-height: 26px;
  }
}
</style>