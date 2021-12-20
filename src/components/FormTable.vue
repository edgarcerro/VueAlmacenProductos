<template>
  <div class="col-sm-6 col-md-4 col-lg-4">
    <form @submit.prevent="createProd">
      <fieldset>
        <legend>Nuevo producto</legend>
        <!-- Aquí los inputs y botones del form -->
        <div class="form-group">
          <label for="id">ID:</label>
          <input type="text" class="form-control" v-model="id" disabled />
        </div>
        <div class="form-group">
          <label for="name">Nombre:</label>
          <input type="text" class="form-control" v-model="name" required />
          <span class="error"></span>
        </div>
        <div class="form-group">
          <label for="units">Unidades:</label>
          <input type="number" class="form-control" v-model="units" />
          <span class="error"></span>
        </div>
        <div class="form-group">
          <label for="price">Precio/u.:</label>
          <input type="number" class="form-control" v-model="price" />
          <span class="error"></span>
        </div>
        <br />
        <button type="submit" class="btn btn-default btn-primary">
          Añadir
        </button>
        <button type="reset" class="btn btn-danger">Reset</button>
      </fieldset>
    </form>
  </div>
</template>


<script>
import api from '../services/api'

export default {
  name: "Form-table",
  data() {
    return {
      id:'',
      name:'',
      price:'',
      units:''
    };
  },
  methods: {
    createProd() {
      let newProd = {
        name: this.name,
        price: this.price,
        units: this.units,
      };
      this.saveNewProd(newProd)
    },
    saveNewProd(newProd){
        api.products.create(newProd)
        .then()
        .catch()
    }
  },
};
</script>


<style>
</style>