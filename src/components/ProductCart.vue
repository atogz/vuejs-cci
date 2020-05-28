<template>
    <div>
        <div v-for="product in products" :key="product.id">
            {{ product.name }} {{ product.price }}
        </div>
        <p>Итоговая сумма корзины: {{ totalSum }}</p>
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
        ]
      }
    },
    methods: {
      addProductToCart(product) {
        this.products.push(product);
      }
    },
    computed: {
      totalSum() {
        return this.products.reduce( (sum, product) => sum + product.price, 0)
      }
    }
  }
</script>

<style scoped>

</style>
