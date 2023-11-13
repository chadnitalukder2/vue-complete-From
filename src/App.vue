<template>
  <div class="app">
    <From @submitBtn="submitted" />
    <Table
      :products="products"
      @deleteProductItem="deleteItem"
      :grentTotal="grentTotal"
    />
  </div>
</template>

<script>
import From from "./components/A_from.vue";
import Table from "./components/A_table.vue";
export default {
  name: "App",
  components: {
    From,
    Table,
  },
  data() {
    return {
      products: JSON.parse(localStorage.getItem("products")) || [],
      grentTotal: 0,
    };
  },

  methods: {
    submitted(productObj) {
      if (
        productObj.id == "" ||
        productObj.name == "" ||
        productObj.brand == "" ||
        productObj.price == "" ||
        productObj.catagory == "" ||
        productObj.quantity == ""
      ) {
        alert("Please fill the from");
        return;
      }
      let data = {
        id: productObj.id,
        name: productObj.name,
        brand: productObj.brand,
        price: productObj.price,
        catagory: productObj.catagory,
        quantity: productObj.quantity,
        total: productObj.price * productObj.quantity,
      };

      this.products.push(data);
      this.calculateTotal();
      this.saveToLocalStorage();
    },
    deleteItem(deleteIndex, text) {
      this.products = this.products.filter(
        (info, Toindex) => Toindex != deleteIndex
      );
      console.log(deleteIndex, "hi", text);
      this.calculateTotal();
      this.saveToLocalStorage();
    },
    saveToLocalStorage() {
      localStorage.setItem("products", JSON.stringify(this.products));
    },
    calculateTotal() {
      let sum = 0;
      for (let i = 0; i < this.products.length; i++) {
        sum += this.products[i].total;
      }
      this.grentTotal = sum;
      this.saveToLocalStorage();
    },
  },
  mounted() {
    this.products = JSON.parse(localStorage.getItem("products"));
    this.calculateTotal();
  },
};
</script>

<style lang="scss">
.app {
  width: 100%;
  margin: 0 auto;
  max-width: 80%;
  margin-top: 20px;
}

.container {
  h1 {
    text-align: center;
    padding: 10px;
    font-size: 30px;
    color: #333;
  }

  form {
    display: flex;
    justify-content: space-between;
    padding: 20px;
    gap: 50px;

    .left {
      flex-basis: 50%;
    }

    .right {
      flex-basis: 50%;
    }

    .box-1 {
      flex-basis: 45%;
      gap: 5%;
      margin: 10px 0;

      @media only screen and (max-width: 576px) {
        flex-basis: 100%;
      }

      label {
        font-size: 18px;
        color: #333;
      }

      input {
        margin-top: 12px;
        margin-bottom: 20px;
        padding: 10px;
        border: 1px solid rgb(147 167 187 / 61%);
        border-radius: 6px;
        line-height: 1.7em;
        width: 100%;
        font-size: 16px;
        font-weight: 400;

        &:focus-visible {
          outline: none;
          color: var(--black-color);
          border-color: #86b7fe;
          outline: 0;
          box-shadow: 0 0 0 0.25rem rgba(255, 107, 0, 0.2);
        }
      }
    }
  }

  .btn {
    text-align: center;

    button {
      margin: 0 auto;
      font-size: 18px;
      font-weight: 200;
      letter-spacing: 1px;
      padding: 13px 30px 13px;
      outline: 0;
      color: #333;
      border: 1px solid rgb(147 167 187 / 61%);
      position: relative;
      background-color: rgba(0, 0, 0, 0);

      &:after {
        content: "";
        background-color: #ffe2d1;
        width: 100%;
        z-index: -1;
        position: absolute;
        height: 100%;
        top: 7px;
        left: 7px;
        transition: 0.2s;
      }

      &:hover:after {
        top: 0px;
        left: 0px;
      }

      @media (min-width: 768px) {
        button {
          padding: 13px 50px 13px;
        }
      }
    }
  }
}

table {
  margin-top: 50px;
  margin-bottom: 100px;
  border-spacing: 0;
  width: 100%;
}

th,
td,
tr {
  padding: 10px 15px;
  border: 1px solid rgb(147 167 187 / 61%);
}

th {
  background: #ffe2d1;
  color: #333;
  text-align: center;
}

table,
th,
td {
  border: 1px solid rgba(147, 167, 187, 0.61);
  border-collapse: collapse;
}

tr:nth-child(odd) td {
  background: rgba(33, 37, 41, 0.07);
}

.delete {
  background: orange;
  font-size: 13px;
  padding: 6px 3px;
  border-radius: 5px;
  margin-right: 10px;
  border: 1px solid rgba(147, 167, 187, 0.61);
}

.edit {
  background: #86b7fe;
  font-size: 13px;
  padding: 6px 8px;

  border-radius: 5px;
  margin-left: 10px;
  border: 1px solid rgba(147, 167, 187, 0.61);
}
</style>
