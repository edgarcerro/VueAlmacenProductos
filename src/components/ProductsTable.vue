<template>
    <div class="hidable row">
            <div class="col-sm-12 col-md-12 col-lg-12" id="almacen">
                <table class="table table-striped table-hover">
                    <thead class="thead-dark bg-light">
                        <tr>
                            <th>Id</th>
                            <th>Nombre</th>
                            <th>Uds.</th>
                            <th>Precio/u</th>
                            <th>Importe</th>
                            <th>Acciones</th>
                        </tr>
                    </thead>
                    <tbody>
                        <product-row
                            v-for="product in products"
                            :key="product.id"
                            :product="product"

                        >
                        </product-row>
                    </tbody>
                    <tfoot>
                        <th colspan="4">Importe total del almacén:</th>
                        <th id="total">0.00 €</th>
                        <th></th>
                    </tfoot>
                </table>
            </div>
        </div>
</template>

<script>
import ProductRow from './ProductRow.vue'
import api from '../services/api'
export default {
  components: { ProductRow },
    name: "Products-table",
    data() {
        return{
            products: []
        }
    },
    mounted(){
        api.products.getAll()
        .then((response) => this.products = response.data)
        .catch((error) => alert(error)
        )}
}
</script>