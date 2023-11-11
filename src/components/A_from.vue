<template>
    <div class="app">

        <div class="container">
    <h1>Hi</h1>
    <form>
      <div class="left">
        <div class="box-1">
          <label>Id: </label>
          <input type="text" class="name" placeholder="id" />
        </div>

        <div class="box-1">
          <label>Name: </label>
          <input type="text" class="name" placeholder="name" />
        </div>
        <div class="box-1">
          <label>Price:</label>
          <input type="text" class="name" placeholder=" price" />
        </div>
      </div>

      <div class="right">
        <div class="box-1">
          <label>Brand:</label>
          <input type="text" class="name" placeholder="brand" />
        </div>
        <div class="box-1">
          <label>Catagory:</label>
          <input type="text" class="name" placeholder="catagory" />
        </div>
        <div class="box-1">
          <label>Quantity:</label>
          <input type="text" class="name" placeholder="quantity" />
        </div>
      </div>
    </form>
    <div class="btn">
        <button >Submit</button>
    </div>


   
 

        </div>

        <table>
        <tr>
          <th>Id</th>
          <th>Name</th>
          <th>Price</th>
          <th>Brand</th>
          <th>Catagory</th>
          <th>Quantity</th>
          <th>..</th>
        </tr>
        <tr>
          <td>name </td>
          <td>age</td>
          <td> info</td>
          <td>gender</td>
          <td>info.about</td>
          <td>info.about</td>
          <td>
            <button>Delete</button>
            <button>Edit</button>
          </td>
        </tr>
        <tr>
          <td>name </td>
          <td>age</td>
          <td> info</td>
          <td>gender</td>
          <td>info.about</td>
          <td>info.about</td>
          <td>
            <button>Delete</button>
            <button>Edit</button>
          </td>
        </tr>
        <tr>
          <td>name </td>
          <td>age</td>
          <td> info</td>
          <td>gender</td>
          <td>info.about</td>
          <td>info.about</td>
          <td>
            <button>Delete</button>
            <button>Edit</button>
          </td>
        </tr>
      </table>
    </div>
  
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.app{
    width: 100%;
  margin: 0 auto;
  max-width: 80%;
  margin-top: 20px;
  
}

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

.btn{
    text-align: center;
    button {
  margin: 0 auto;
  font-size: 18px;
  font-weight: 200;
  letter-spacing: 1px;
  padding: 13px 30px 13px;
  outline: 0;
  color:#333;
  border:1px solid rgb(147 167 187 / 61%) ;
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

table {
    margin-top: 50px;
    margin-bottom: 100px;
  border-spacing: 0;
  width: 100%;
}

th,
td, tr{
  padding: 10px 15px;
  border:1px solid rgb(147 167 187 / 61%);
}
th {
  background: #ffe2d1;
  color: #333;
  text-align: center;
}
table,
  th,
  td {
    border: 1px solid #86b7fe;
    border-collapse: collapse;
  }

tr:nth-child(odd) td {
  background: rgba(33, 37, 41, 0.07);
}


</style>
