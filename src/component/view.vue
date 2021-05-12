<template>
  <div class="breadcrumbs">
    <router-link to="/main" class="text-white">Вернуться к списку</router-link>
  </div>
  <div class="card">
    <div>
      <p><strong>Фамилия:</strong> {{}}</p>
      <p><strong>Имя:</strong> {{}}</p>
      <p><strong>"Электронная почта:</strong> {{}}</p>
    </div>
    <div>
      <img src="#" title="dsa">
    </div>
  </div>
</template>

<script>
import {inject, ref} from 'vue'
import { useRoute } from 'vue-router'
export default {
  setup() {
    const people = inject('people')
    const route = useRoute()
    const peopleList = ref(route)
    return{
      people,
      peopleList
    }
  },

  name: "view"
}
</script>

<style scoped>

</style>