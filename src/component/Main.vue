<template>
  <div class="card">
    <div class="header">
      <h1>Список пользователей</h1>
      <button class="btn primary" @click="flag = true">Создать</button>
    </div>
    <Suspense>
      <RequestTable />
    </Suspense>
<!--    <teleport to="body" >-->
<!--      <request-modal-->
<!--          v-if="flag"-->
<!--          :last-name="people.last_name"-->
<!--          :first-name="people.first_name"-->
<!--          :email="people.email"-->
<!--          @create-list="Submit"-->
<!--          @cancel="flag = false"-->
<!--      />-->
<!--    </teleport>-->
  </div>

</template>

<script>
import RequestModal from "@/component/RequestModal"
import RequestTable from "@/component/RequestTable"

export default {
  components: { RequestModal, RequestTable }
}
</script>
