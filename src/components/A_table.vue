<template>
     <table>
          <tr>
              <th>Id</th>
              <th>Name</th>
              <th>Brand</th>
              <th>Catagory</th>
              <th>Price</th>
              <th>Quantity</th>
              <th>Total</th>
              <th>..</th>
          </tr>
          <tr v-for="(product, index) in products" :key="index">
              <td> {{product.id}} </td>
              <td>{{product.name}}</td>
              <td>{{product.brand}}</td>
              <td>{{product.catagory}}</td>
              <td> {{product.price}}</td>
              <td>{{product.quantity}}</td>
              <td>{{product.total}}</td>
              <td>
                  <button @click="puja(index)" class="delete">Delete</button>
                  <button class="edit">Edit</button>
              </td>
          </tr>
  
      </table>
</template>

<script>
    export default {
        name:"A_table",
        props:[
            'products'
        ],
        methods:{
        puja(index){
                this.$emit("deleteProductItem",index, "hello")
            
          }
        }
    }
</script>

<style lang="scss" scoped>

</style>