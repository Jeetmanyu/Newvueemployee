<template>
       <div>
        <h1>Employee Details</h1>
      <div class="row">
          <div class="col-md-10"></div>
          <div class="col-md-2">
            <router-link :to="{ name: 'CreateItem' }" class="btn btn-primary">Create employee</router-link>
          </div>
        </div><br />
<div class="row">
  <div class="col-lg-6">
  </div>
</div>
        <table class="table table-hover">
            <thead>
            <tr>
                <td>Emp ID</td>
                <td>First Name</td>
                <td>Last name</td>
                <td>Dob</td>
                <td>Email</td>
                <td>Gender</td>
                <td>City</td>
                <td>Mobile</td>
                <td>Designation:</td>
                <td>Actions</td>
            </tr>
            </thead>

            <tbody>
                <tr v-for="item in items" :key="item.employeeId">
                    <td>{{ item.employeeId }}</td>
                    <td>{{ item.firstName }}</td>
                    <td>{{ item.lastName }}</td>
                    <td>{{ item.dob }}</td>
                    <td>{{ item.email }}</td>
                    <td>{{ item.gender}}</td>
                     <td>{{ item.city}}</td>
                     <td>{{ item.mobile}}</td>
                     <td>{{ item.designation}}</td>
                    <td><router-link :to="{name: 'EditItem', params: { id: item.employeeId }}" class="btn btn-primary">Edit</router-link></td>
                    <td><button class="btn btn-danger" v-on:click="deleteItem(item.employeeId)">delete</button> </td>
                </tr>
            </tbody>
      </table>
    </div>
</template>

<script>
export default {
  data () {
    return {
      items: [],
      search: ''
    }
  },
  created: function () {
    this.fetchItems()
  },
  methods: {
    fetchItems () {
      let uri = 'http://localhost:8090/employees'
      this.axios.get(uri).then((response) => {
        this.items = response.data
      })
    },
    deleteItem (employeeId) {
      // subhma url
      let uri = 'http://localhost:8090/employees/' + employeeId
      // this.items.splice(0, 1)
      this.axios.delete(uri, JSON.stringify(this.userdata), {
        headers: {
          'Access-Control-Allow-Origin': '*',
          'Content-Type': 'application/json'
        }
      }).then((response) => {
        this.$router.go()
        // dthis.$router.push({name: 'DisplayItem'})
      })
    }
  }
}
</script>
