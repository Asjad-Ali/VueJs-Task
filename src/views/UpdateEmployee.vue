<template>
    <div class="container text-center my-5">
    <h1 class="my-5">Update Employee</h1>
    <div class="row">
        <div class="row d-flex justify-content-center ">
          <div class="col-6 border p-5 rounded border-2">
            <div class="row text-start mb-2">
              <div class="col-12 mb-3">
              <label>Name </label>
              <input
              v-model="emp.name"
                  type="text"
                  name="name"
                  id="name"
                  class="form-control input-alignment"
              />
              </div>
              <div class="col-6 mb-3">
              <label>Designation </label>
              <input
                  v-model="emp.designation"
                  type="text"
                  class="form-control input-alignment"
                  name="Designation"
              />
              </div>
              <div class="col-6 mb-3">
              <label>Salary </label>
              <input
                  v-model="emp.salary"
                  type="number"
                  class="form-control input-alignment"
                  name="salary"
              />
              </div>
              <div class="col-6 mb-3">
              <div class="position-relative">
                  <label> Gender</label>
                  <select
                  v-model="emp.gender" 
                  class="form-select"
                  aria-label="Default select example"
                  >
                  <option selected value="" disabled>Select Gender</option>
                  <option v-for="gen in gender" :key="gen"
                  :selected=" gen.value == emp.gender"
                  :value="gen.value"
                  >{{ gen.value }}</option>
                  </select>
              </div>
              </div>
              <div class="col-6 mb-3">
              <div class="position-relative">
                  <label> Status</label>
                  <select
                  v-model="emp.status"
                  class="form-select"
                  aria-label="Default select example">
                  <option selected value="" disabled>Select Status</option>
                  <option v-for="stats in status" :key="stats"
                  :selected=" stats.value == emp.status" :value="stats.value"
                  >{{ stats.value }}</option>
                  </select>
              </div>
              </div>
            </div> 
            <div class="row">
              <div>
                <router-link to="/">
                  <button
                  type="button"
                  class="btn btn-secondary text-white me-3"  data-bs-dismiss="modal">
                  back
                  </button>
                </router-link>
                  <button @click="updateEmployee" data-bs-dismiss="modal" type="button" class="btn btn-primary text-white">Update Employee</button>
              </div>
            </div>
          </div>
        </div>
    </div>
    </div>
</template>

<script>
import { reactive, ref } from '@vue/reactivity'
import { useStore } from 'vuex'
import { computed } from '@vue/runtime-core'
export default{
  props:{
    empData:{
      type: Object,
      required: true
    }
  },
  setup(props){
    const store = useStore()
    console.log("Employee",props.empData)
      const emp = reactive({
            id: '',
            name: '',
            designation: '',
            salary: '',
            gender: '',
            status: '',
      })

      const selectedEmployee = ref(computed(() => store.getters.getSelectedEmployee))
      console.log("IN Update",selectedEmployee.value)
      emp.id = selectedEmployee.value.id
      emp.name = selectedEmployee.value.name
      emp.designation = selectedEmployee.value.designation
      emp.salary = selectedEmployee.value.salary
      emp.gender = selectedEmployee.value.gender
      emp.status = selectedEmployee.value.status

      const gender = [
        {value:"Male"},
        {value:"Female"}
      ]
      const status = [
        {value:"Completed"},
        {value:"Not Completed"}
      ]

      const updateEmployee = () =>{
        console.log(emp)
          store.dispatch("updateEmployeeData",emp);
      }
    return{
      updateEmployee,
      emp,
      gender,
      status
    }
  }
}

</script>

<style scoped>
label {
  margin-bottom: 5px;
}
</style>