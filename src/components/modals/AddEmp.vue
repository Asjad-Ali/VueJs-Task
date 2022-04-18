<template>
  <!-- Add Employee Modal -->
  <div class="container-xl">
  <div
    class="modal fade "
    id="addModal"
    tabindex="-1"
    aria-labelledby="exampleModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog form pa-4 modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header d-flex justify-center">
          <h5 class="modal-title" id="exampleModalLabel">Add Employee</h5>
        </div>
        <div class="modal-body text-start">
          <div class="row mb-2">
            <div class="col-12 mb-3">
              <label> Name </label>
              <input
              v-model="employee.name"
                type="text"
                name="name"
                id="name"
                class="form-control input-alignment"
                required
              />
            </div>
            <div class="col-6 mb-3">
              <label>Designation </label>
              <input
                v-model="employee.designation"
                type="text"
                class="form-control input-alignment"
                name="Designation"
                required
              />
            </div>
            <div class="col-6 mb-3">
              <label>Salary </label>
              <input
                v-model="employee.salary"
                type="number"
                class="form-control input-alignment"
                name="salary"
                required
              />
            </div>
            <div class="col-6 mb-3">
              <div class="position-relative">
                <label> Gender</label>
                <select
                  v-model="employee.gender" 
                  required
                  class="form-select"
                  aria-label="Default select example"
                >
                  <option selected disabled value="">Select Gender</option>
                  <option value="Male">Male</option>
                  <option value="Female">Female</option>
                </select>
              </div>
            </div>
            <div class="col-6 mb-3">
              <div class="position-relative">
                <label> Status</label>
                <select
                  v-model="employee.status"
                  required
                  class="form-select"
                  aria-label="Default select example"
                >
                  <option selected disabled value="">Select Status</option>
                  <option value="Completed">Completed</option>
                  <option value="Not Completed">Not Completed</option>
                </select>
              </div>
            </div>
          </div>
        </div>
        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary text-white"
            data-bs-dismiss="modal"
          >
            Close
          </button>
          <button @click="addEmployee"  type="submit" class="btn btn-primary text-white">Add Employee</button>
        </div>
      </div>
    </div>
  </div>
  </div>
</template>

<script setup>
const {  ref }=require("@vue/reactivity");
const { useStore }=require("vuex");
  const store = useStore()
  var employee = ref({
      name: "",
      designation: "",
      salary: "",
      gender: "",
      status: "",
})
  const addEmployee = () =>{
      store.dispatch("addEmployeeData",employee.value);
      employee.value = []
  }
</script>

<style scoped>
label {
  margin-bottom: 5px;
}
</style>
