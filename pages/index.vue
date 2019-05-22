<template>
<section class="container">
  <div class="columns is-multiline">
    <!-- v-for で breed_list からループ出力 -->
    <div v-for="(item, i) in breed_list" v-bind:key='i' class="culumn is-2">
      <a class="button">{{ i }}</a>
    </div>
  </div>
</section>
</template>

<script>
import AppLogo from '~/components/AppLogo.vue'
import dogApi from '@/api/dog'
import { mapState } from 'vuex';

export default {
  components: {
    AppLogo
  },
  async fetch({
    store
  }) {
    let json = await dogApi.breeds();
    store.commit('breed_list_update', json);
  },
  computed: mapState(['breed_list']), // mapState ヘルパー
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
