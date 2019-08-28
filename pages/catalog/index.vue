<template>
  <main>
    <h1 class="mb-4">
      Каталог товаров
    </h1>
    <div class="row">
      <div v-for="item in products" :key="item.id" class="col-sm-4">
        <div class="card mb-4" style="background: red">
          <div class="card-header">
            {{ item.title }}
          </div>
          <div class="card-body">
            <p>{{ item.price }} руб.</p>
            <nuxt-link :to="'/catalog/' + item.id + '/'">
              Подробнее
            </nuxt-link>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  computed: {
    products() {
      return this.$store.state.products;
    },
  },
  async asyncData({ store }) {
    await store.dispatch("LOAD_PRODUCTS");
  },
};
</script>
