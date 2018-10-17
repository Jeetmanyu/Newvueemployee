<template>
  <div>
    <h1>Employee Details</h1>
    <form v-on:submit.prevent="AddDetails">
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label>first name:</label>
              <input type="text" class="form-control col-md-6" v-model="userdata.firstName" required />
            </div>
          </div>
        </div><br />
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label>Last name:</label>
              <input type="text" class="form-control col-md-6" v-model="userdata.lastName" required />
            </div>
          </div>
        </div><br />
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label>Dob:</label>
              <input type="date" class="form-control col-md-6" v-model="userdata.dob" required />
            </div>
          </div>
        </div><br />
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label>Email:</label>
              <input type="email" class="form-control col-md-6" v-model="userdata.email" required />
            </div>
          </div>
        </div><br />
         <div class="row">
          <div class="col-md-6">
            <div class="form-group">
            <label><h4>Gender:</h4></label>
            <input type="radio" id="male" value="male" v-model="userdata.gender">
            <label for="one"><h4>Male</h4></label>
           <input type="radio" id="female" value="female" v-model="userdata.gender">
           <label for="two"><h4>Female</h4></label>
            </div>
          </div>
        </div><br />
         <div class="row">
        <div class="col-md-2">
      <div class="form-group">
        <label>City:</label>
        <select class="form-control col-md-2" v-model="userdata.city">
       <option>Delhi</option>
       <option>Mumbai</option>
       <option>Chennai</option>
       <option>Kolkata</option>
       <option>Gwalior</option>
       <option>Jaipur</option>
     </select>
     </div>
     </div>
     </div> <br/>
     <div class="row">
          <div class="col-md-2">
            <div class="form-group">
              <label>Mobile_no:</label>
              <input type="text" class="form-control col-md-2" v-model="userdata.mobile" required />
            </div>
          </div>
        </div><br />
          <div class="row">
        <div class="col-md-2">
      <div class="form-group">
        <label>Designation:</label>
        <select class="form-control col-md-2" v-model="userdata.designation">
       <option>Ceo</option>
       <option>Manager</option>
       <option>TeamLeader</option>
       <option>GroupLeader</option>
       <option>Developer</option>
       <option>Tester</option>
     </select>
     </div>
     </div>
     </div> <br/>
         <div class="form-group">
          <button class="btn btn-primary">Add Emp details</button>
        </div>
    </form>
  </div>
</template>

<script>

export default {
  data () {
    return {
      userdata: {}
    }
  },
  methods: {
    AddDetails () {
      // subhma url
      let uri = 'http://localhost:8090/employees'
      this.axios.post(uri, JSON.stringify(this.userdata), {
        headers: {
          'Access-Control-Allow-Origin': '*',
          'Content-Type': 'application/json'
        }
      }).then((response) => {
        this.$router.push({name: 'DisplayItem'})
      })
    }
  }
}
</script>
