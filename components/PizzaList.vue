<template>
  <div class="flex flex-wrap justify-between">
    <div v-for="obj of pizzas" :key="obj.id" class="w-full lg:w-1/4 p-4 my-3">
      <img :src="obj.images[1]" alt="">
      <div>
        <p class="text-2xl font-medium">
          {{ obj.title }}
        </p>
        <p class="text-sm h-24 my-3">
          {{ obj.desc }}
        </p>
        <div class="flex items-center justify-between">
          <p class="text-2xl font-medium">
            от {{ obj.price }} тг.
          </p>
          <button class="text-main bg-orange-100 py-2 px-4 rounded-full">
            Выбрать
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PizzaList',
  data () {
    return {
      pizzas: []
    }
  },
  async fetch () {
    this.pizzas = await fetch(
      'http://localhost:3001/pizza'
    ).then(res => res.json())
  }
}
</script>
