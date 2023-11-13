<template>
  <div class="container">
          <h1>From</h1>
          <form>
              <div class="left">
                  <div class="box-1">
                      <label>Id: </label>
                      <input v-model="id" type="text" class="name" placeholder="id" />
                  </div>
  
                  <div class="box-1">
                      <label>Name: </label>
                      <input v-model="name" type="text" class="name" placeholder="name" />
                  </div>
                  <div class="box-1">
                      <label>Price:</label>
                      <input v-model="price" type="text" class="name" placeholder=" price" />
                  </div>
              </div>
  
              <div class="right">
                  <div class="box-1">
                      <label>Brand:</label>
                      <input v-model="brand" type="text" class="name" placeholder="brand" />
                  </div>
                  <div class="box-1">
                      <label>Catagory:</label>
                      <input v-model="catagory" type="text" class="name" placeholder="catagory" />
                  </div>
                  <div class="box-1">
                      <label>Quantity:</label>
                      <input v-model="quantity" type="text" class="name" placeholder="quantity" />
                  </div>
              </div>
          </form>
          <div class="btn">
              <button @click="submitted()">Submit</button>
          </div>

      </div>
</template>

<script>

    export default {
        name: "A_from",
      data() {
          return {
        
              id: "",
              name: "",
              brand:"",
              price: "",
              catagory: "",
              quantity: "",
              total : "",

          
          }
      },
      
   methods:{
    submitted(){
        let productObj = {
            id: this.id,
            name: this.name,
            brand:this.brand,
              price: this.price,
              catagory: this.catagory,
              quantity: this.quantity,
              total : this.total,
        }
        this.$emit("submitBtn",productObj)
        console.log('submitBtn')
     
                  this.id = "" ,
                  this.name = "" ,
                  this.brand = "" ,
                  this.price = "" ,
                 this.catagory = "" ,
                  this.quantity = ""
    }
   }
        
    }
</script>

<style lang="scss" scoped>

</style>