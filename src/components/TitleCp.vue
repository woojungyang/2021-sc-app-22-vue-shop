<template>
  <header class="header-wrapper">
    <h1 class="logo-wrap"></h1>
    <img src="@/assets/img/logo/png" alt="logo" class="logo">
    {{mainTitle}}

  </header>
</template>

<script>
export default {
  name: 'TitleCp',
  props: ['title'],
};
</script>

<style lang="scss" scoped>
.header-wrapper{
  padding:$gutter-wdith;
  background-color: $secondary-color;
  color:$primary-color;
  font-size:1.5em;
  .logo{
    width:1.5em
  }
}

</style>
