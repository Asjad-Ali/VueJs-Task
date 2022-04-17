<template>
  <div class="container my-4">
    <div class="mb-4">
      <h1 class="text-center">
        <span class="border-bottom">VueJs Task</span>
      </h1>
    </div>
    <div class="card rounded shadow-sm py-3">
      <div class="card-body">
        <EmployeesTable />
      </div>
    </div>
    <DeleteEmp />
    <AddEmployeeModal />
  </div>
</template>

<script setup>
import EmployeesTable from "@/components/EmployeesTable.vue";
import DeleteEmp from '@/components/modals/deleteEmp.vue';
import AddEmployeeModal from '../components/modals/AddEmp.vue';
</script>

<style scoped>

</style>