<template>
  <div class="form-control">
    <br>
    <label for="search"></label>
    <input type="text" placeholder="Поиск по имени" id="search" v-model.trim="filter">
    <hr/>
    <table class="table">
      <thead>
      <tr>
        <th>№</th>
        <th>Фамилия</th>
        <th>Имя</th>
        <th>E-mail</th>
        <th>Действия</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(person, id) in Filters" :key="person.id">
        <td>{{ id+1}}</td>
        <td>{{ person.last_name }}</td>
        <td>{{ person.first_name }}</td>
        <td>{{ person.email }}</td>
        <td>
          <router-link :to="'/table/'+person.id" v-slot="navigator">
            <button class="btn" @click="navigator">Посмотреть</button>
          </router-link>
          <button class="btn danger" @click="remove">Удалить</button>
        </td>
      </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import { inject, ref, computed } from 'vue'
export default {
  setup() {
    const peopleList = inject('people')
    const filter = ref('')
    function remove(idx) {
      const element = peopleList.value.filter(el=> el.id !== idx)
      peopleList.value.splice(element,1)
    }
    return{
      peopleList,
      remove,
      filter,
      Filters: computed(()=> {
        return peopleList.value.filter( el => {
          return el.first_name[0].toLowerCase().includes(filter.value.toLowerCase())
        })
      })
    }
  }
}
</script>

<style scoped>

</style>