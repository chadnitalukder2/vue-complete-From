<template>
<div class="app">

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
        <tr v-for="(info, index) in details" :key="index">
            <td> {{info.id}} </td>
            <td>{{info.name}}</td>
            <td> {{info.price}}</td>
            <td>{{info.brand}}</td>
            <td>{{info.catagory}}</td>
            <td>{{info.quantity}}</td>
            <td>
                <button class="delete">Delete</button>
                <button class="edit">Edit</button>
            </td>
        </tr>

    </table>
</div>
</template>

<script>
export default {
    name: "A_from",
    data() {
        return {
            id: "",
            name: "",
            brand: "",
            price: "",
            catagory: "",
            quantity: "",
            details: []
        }
    },

    methods: {
        submitted() {
            if (
                this.id == "" ||
                this.name == "" ||
                this.brand == "" ||
                this.price == "" ||
                this.catagory == "" ||
                this.quantity == ""
            ){ 
                alert("Please fill the from")
            return; 

            }
            let data = {
                id: this.id,
                name: this.name,
                brand: this.brand,
                price: this.price,
                catagory: this.catagory,
                quantity: this.quantity
            }
            this.details.push(data);
            this.id = "" ,
                this.name = "" ,
                this.brand = "" ,
                this.price = "" ,
                this.catagory = "" ,
                this.quantity = ""
        }
    },
    mounted(){
        let data = [
            {
                id: "12345",
                name: "Bag",
                price: "540",
                brand:"VIP",
                catagory: "Bag",
                quantity: "4"

            }
        ];
        this.details = data
    }
};
</script>

<style lang="scss" scoped>
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
