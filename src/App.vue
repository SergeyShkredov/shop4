<template>
<!--  <Navbar-->
<!--      :cartCount="cartCount"-->
<!--      @resetCartCount="resetCartCount"-->
<!--      v-if="!['Signup', 'Signin'].includes($route.name)"-->
<!--  />-->

  <div style="min-height: 60vh">
    <div style="min-height: 60vh">
      <router-view
          v-if="products  && categories"
          :products="products"
          :categories="categories"
          @getProducts="getProducts"
          @getCategories="getCategories"
      >
      </router-view>
    </div>
  </div>

</template>

<script>
import ProductService from "@/services/productService";
import Navbar from "@/components/Navbar";

export default {
  data() {
    return {
      products: null,
      categories: null,
      key: 0,
    };
  },

  methods: {
    async getProducts() {
      ProductService.getAllProducts()
          .then(response => {
            this.products = response.data
          })
          .catch(e => {
            alert(e)
          })
    },

    async getCategories() {
      ProductService.getCategories()
          .then(response => {
            this.categories = response.data
          })
          .catch(e => {
            alert(e)
          })
    },

  },
  mounted() {
    this.getProducts()
    this.getCategories()
  },
  components: {
    Navbar
  }
};
</script>

<style>
html {
  overflow-y: scroll;
}
</style>
