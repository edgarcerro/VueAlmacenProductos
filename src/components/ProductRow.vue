<template>
  <tr>
    <td>{{ product.id }}</td>
    <td>{{ product.name }}</td>
    <td>{{ product.units }}</td>
    <td>{{ product.price }}</td>
    <td>{{ productImport }} €</td>

    <td>
      <button class="increase btn btn-secondary" @click="chgUnits(1)">
        <i class="bi bi-arrow-up"></i>
      </button>
      <button class="decrease btn btn-secondary" @click="chgUnits(-1)">
        <i class="bi bi-arrow-down"></i>
      </button>
      <button @click="editForm()" class="edit btn btn-secondary">
        <i class="bi bi-pencil"></i>
      </button>
      <button
        @click="deleteProduct(product.id)"
        class="delete btn btn-secondary"
      >
        <i class="bi bi-trash"></i>
      </button>
    </td>
  </tr>
</template>

<script>
import api from '../services/api'
export default {
    name: "Product-row",
    props: ['product'],
    computed: {
        productImport(){
           return (this.product.units * this.product.price)
        }
    },
    methods:{
        chgUnits(units){
            
            api.products.modify({
                id:this.product.id,
                name:this.product.name,
                units: this.product.units+Number(units),
                price: this.product.price
            })
            .then()
            .catch()
        },

        deleteProduct(id){
            if(confirm('Seguro que quieres borrar el producto con id: '+ id)){
                api.products.delete(id)
                .then()
                .catch()
            }
            
            
        },

        editForm(){

        }
    }
}
</script>

<style>
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.7.2/font/bootstrap-icons.css");
</style>