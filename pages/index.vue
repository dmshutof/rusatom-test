<template>
  <div>
    <nuxt-link to="/add">Перейти на страницу Add</nuxt-link>
  </div>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
<style lang="scss" scoped>
a{
    position: absolute;
    left: 50px;
    top: 50px;
    transform: translate(-50%,-50%);
    font-weight: 800;
    font-size: 28px;
    line-height: 32px;
    text-align: center;
    color: #FFFFFF;
}
</style>
