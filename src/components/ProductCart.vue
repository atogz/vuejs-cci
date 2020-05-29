<template>
    <div>
        <div v-for="(product, index) in products" :key="product.id">
            {{ product.name }} {{ product.price }}
            <button @click="deleteProduct(index)">Удалить</button>
        </div>
        <p>Итоговая сумма корзины: {{ totalSum }}</p>

        <transition name="fade">
            <div v-show="totalSum > 3000">Сумма больше 3000</div>
        </transition>


        <input type="text" v-model="userInput"/>
        <button @click="addProductToCart({id:4, name: 'Новый товар', price: 2000})">Добавить товар в корзину</button>

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
