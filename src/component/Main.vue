<template>
  <div class="card">
    <div class="header">
      <h1>Список пользователей</h1>
      <button class="btn primary" @click="flag = true">Создать</button>
    </div>
    <RequestTable/>
    <teleport to="body" >
      <request-modal
          v-if="flag"
          :last-name="people.last_name"
          :first-name="people.first_name"
          :email="people.email"
          @create-list="Submit"
          @cancel="flag = false"
      />
    </teleport>
  </div>

</template>

<script>
import RequestModal from "@/component/RequestModal";
import RequestTable from "@/component/RequestTable";
import { ref, provide } from 'vue'
// import { useRouter } from 'vue-router'
export default {
  setup() {
    const flag = ref(false)
    const people = ref([
      {id: 1, last_name:"Bluth",first_name:"George",email:"george.bluth@reqres.in", avatar:"https://reqres.in/img/faces/1-image.jpg"},
      {id: 2, last_name:"Weaver",first_name:"Janet",email:"janet.weaver@reqres.in",avatar:"https://reqres.in/img/faces/2-image.jpg"},
      {id: 3, last_name:"Wong",first_name:"Emma",email:"emma.wong@reqres.in",avatar:"https://reqres.in/img/faces/3-image.jpg"},
      {id: 4, last_name:"Holt",first_name:"Eve",email:"eve.holt@reqres.in",avatar:"https://reqres.in/img/faces/4-image.jpg"},
      {id: 5, last_name:"Morris",first_name:"Charles",email:"charles.morris@reqres.in",avatar:"https://reqres.in/img/faces/5-image.jpg"},
      {id: 6, last_name:"Ramos",first_name:"Tracey",email:"tracey.ramos@reqres.in",avatar:"https://reqres.in/img/faces/6-image.jpg"}
    ])
    provide('people', people)
    // const router = useRouter()
    const Submit = (payload) => {
      people.value.push(payload)
      flag.value = false
    }


    return {
      people,
      Submit,
      flag
    }
  },
  components: {RequestModal, RequestTable}
}
</script>


<style scoped>

</style>