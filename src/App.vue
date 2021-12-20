<template>
  <div>
    <app-nav></app-nav>
    <div class="container">
      <header>
        <h1>Almacén central de productos - ACME SL</h1>
      </header>
    </div>
    <products-table>
      <product-row></product-row>
    </products-table>
    <br>
    <form-table></form-table>
  </div>
</template>

<script>
import AppNav from "./components/AppNav.vue";
import FormTable from "./components/FormTable.vue";
import ProductRow from "./components/ProductRow.vue";
import ProductsTable from "./components/ProductsTable.vue";

export default {
  name: "App",
  components: {
    AppNav,
    ProductsTable,
    ProductRow,
    FormTable,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
