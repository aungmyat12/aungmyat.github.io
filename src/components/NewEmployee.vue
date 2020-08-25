<template>
  <div id="new-employee">
    <h3>New Employee</h3>
    <div class="row">
      <form @submit.prevent="saveEmployee" class="col s12">
        <div class="row">
          <div class="input-field col s12">
            <input type="text" id="id" v-model="employee_id" required>
            <label for="id">Employee ID#</label>
          </div>
        </div>
        <div class="row">
          <div class="input-field col s12">
            <input type="text" id="name" v-model="name" required>
            <label for="name">Name</label>
          </div>
        </div>
        <div class="row">
          <div class="input-field col s12">
            <input type="text" id="department" v-model="department" required>
            <label for="department">Department</label>
          </div>
        </div>
        <div class="row">
          <div class="input-field col s12">
            <input type="text" id="position" v-model="position" required>
            <label for="position">Position</label>
          </div>
        </div>
        <button type="submit" class="btn">Submit</button>
        <router-link to="/" class="btn grey">Cancel</router-link>
      </form>
    </div>
  </div>
</template>

<script>
  import db from './firebaseinit';
  export default {
    name: "new-employee",
    data() {
      return {
        employee_id: null,
        name: null,
        department: null,
        position: null
      }
    },
    methods: {
      saveEmployee () {
        db.collection('employees').add({
          employee_id: this.employee_id,
          name: this.name,
          department: this.department,
          position: this.position
        })
        .then(docRef => this.$router.push('/'))
        .catch(err => console.log(err));
      }
    }
  }
</script>

<style scoped>

</style>
