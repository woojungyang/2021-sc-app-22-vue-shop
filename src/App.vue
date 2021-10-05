<template>
  <div class="container my-3">
    <TitleCp :title="mainTitle" />
  </div>
</template>

<script>
import TitleCp from './components/TitleCp.vue';

export default {
  name: 'App',
  data() {
    return {
      mainTitle: '다팔아 쇼핑몰',
    };
  },
  components: { TitleCp },
};
</script>

<style lang="scss">

</style>
