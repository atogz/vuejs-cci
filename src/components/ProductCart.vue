<template>
    <div class="w-full flex space-x-3 md:space-x-12 cursor-pointer">
        <div class="flex flex-col border-2 border-gray-400 p-6 hover:bg-accentColor rounded w-1/3" v-for="product in products" :key="product.id">
            <span>{{ product.name }}</span>
            <span>{{ product.price }}</span>
        </div>
    </div>
</template>

<script>
  export default {
    name: "ProductCart",
    data() {
      return {
        products: [
          {id: 1, name: 'Товар 1', price: 200},
          {id: 2, name: 'Товар 2', price: 400},
          {id: 3, name: 'Товар 3', price: 600},
        ],
        userInput: '',
      }
    },
    methods: {
      addProductToCart(product) {
        this.products.push(product);
      },
      deleteProduct(index) {
        this.products.splice(index, 1);
      }
    },
    computed: {
      totalSum() {
        return this.products.reduce( (sum, product) => sum + product.price, 0)
      }
    },

    watch: {
        userInput: function () {
            if(this.userInput.length > 3) {
              alert('userInput больше 3 символов!')
            }
        }
    }
  }
</script>

<style scoped>

    .bounce-enter-active {
        animation: bounce-in .5s;
    }
    .bounce-leave-active {
        animation: bounce-in .5s reverse;
    }
    @keyframes bounce-in {
        0% {
            transform: scale(0);
        }
        50% {
            transform: scale(1.5);
        }
        100% {
            transform: scale(1);
        }
    }

    .fade-enter-active, .fade-leave-active {
        transition: opacity 1.5s;
    }
    .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
        opacity: 0;
    }

</style>
