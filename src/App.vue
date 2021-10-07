<template>
  <div class="container my-3">
    <Title :title="mainTitle" />
    <Search @@change="onChangeQuery" />
    <ListWrap @@click="onChangeList" :lists="searchFoods" />
    <Modal v-show="isSelected" :list="food" @@close="onCloseModal" />
  </div>
</template>

<script>
import axios from 'axios';
import Title from './components/TitleCp.vue';
import Search from './components/SearchCp.vue';
import ListWrap from './components/ListWrapCp.vue';
import Modal from './components/ModalCp.vue';

export default {
  name: 'App',
  components: {
    Title,
    Search,
    ListWrap,
    Modal,
  },
  data() {
    return {
      mainTitle: '다팔아 쇼핑몰',
      foods: [],
      food: {},
      isSelected: false,
      searchFoods: [],
    };
  },
  async created() {
    const { data } = await axios.get('/json/foods.json');
    this.foods = data;
    this.searchFoods = data;
  },
  methods: {
    onChangeQuery(query) {
      this.searchFoods = this.foods.filter((v) => {
        const result = v.title.toLowerCase().includes(query.toLowerCase())
                        || v.description.toLowerCase().includes(query.toLowerCase())
                        || v.price.toLowerCase().includes(query.toLowerCase());
        return result;
      });
    },
    onChangeList(v) {
      this.food = v;
      this.isSelected = true;
    },
    onCloseModal() {
      this.isSelected = false;
    },
  },
};
</script>

<style lang="scss">
/* 여기에 주석이라도 있어야 scss-loader가 실행된다. */
</style>
