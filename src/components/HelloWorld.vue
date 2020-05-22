<template>
  <div class="hello" >
      <div v-if="rendered">
          {{ message }}
      </div>
      {{ rendered }}
    <button @click="rendered = !rendered">Изменить состояние</button>
  </div>
</template>

<script>
export default {

  name: 'HelloWorld',

  data() {
    return {
      message: 'Hello',
      secondMessage: '213',
      products: [],
      rendered: false
    }
  },

  methods: {
    changeMessage(newValue) {
      this.message = newValue
    }
  },

  mounted() {
    this.message = 'Тест';
  }

}
</script>


<style scoped>
    .hello {
        color: red
    }

</style>
