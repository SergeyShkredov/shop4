<template>

  <div>
    <div class="card-body">

        <h4 class="card-title">{{ product.productName }}</h4>
        <div class="card-text">{{ product.productCategory }}</div>
        <div class="card-text">{{ product.productPrice }}</div>

      <router-link :to="{ name: 'ShowDetails', params: { id: product.productId } }"
      ><h5 class="card-title">{{ product.productName }}</h5></router-link>

    </div>
  </div>

</template>

<script>
export default {
  name: "ProductBox",
  props: ["product"],
  methods: {
    showDetails() {
      this.$router.push({
        name: "ShowDetails",
        params: { id: this.product.productId },
      });
    },
  },
};
</script>

<style scoped>

</style>
