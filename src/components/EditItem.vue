<template>
    <div>
        <h1>Update</h1>
        <div class="row">
          <div class="col-md-10"></div>
          <div class="col-md-2"><router-link :to="{ name: 'DisplayItem' }" class="btn btn-success">Return to Items</router-link></div>
        </div>

        <form v-on:submit.prevent="update">
            <div class="form-group">
                <label>Emp Id</label>
                <input type="text" class="form-control" v-model="userdata.employeeId">
            </div>
            <div class="form-group">
                <label>Frist name</label>
                <input type="text" class="form-control" v-model="userdata.firstName">
            </div>

            <div class="form-group">
                <label>Last name</label>
                <input type="text" class="form-control" v-model="userdata.lastName">
            </div>
             <div class="form-group">
                <label>Dob</label>
                <input type="text" class="form-control" v-model="userdata.dob">
            </div>
            <div class="form-group">
                <label>email</label>
                <input type="text" class="form-control" v-model="userdata.email">
            </div>
            <div class="form-group">
            <label>Gender:</label>
            <input type="radio" id="male" value="male" v-model="userdata.gender">
            <label for="one">Male</label>
           <input type="radio" id="female" value="female" v-model="userdata.gender">
           <label for="two">Female</label>
            </div><br/>
             <div class="form-group">
        <label>City:</label>
        <select class="form-control " v-model="userdata.city">
       <option>Delhi</option>
       <option>Mumbai</option>
       <option>Chennai</option>
       <option>Kolkata</option>
         <option>Gwalior</option>
       <option>Jaipur</option>
     </select>
     </div> <br/>
     <div class="form-group">
        <label>Designation:</label>
        <select class="form-control " v-model="userdata.designation">
       <option>Ceo</option>
       <option>Manager</option>
       <option>TeamLeader</option>
       <option>GroupLeader</option>
       <option>Developer</option>
       <option>Tester</option>
     </select>
     </div> <br/>
      <div class="form-group">
              <label>Mobile_no:</label>
              <input type="text" class="form-control col-md-4" v-model="userdata.mobile" required />
            </div><br/><br/>
        <div class="form-group">
                <button class="btn btn-primary">Update</button>
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
  created: function () {
    this.getItem()
  },
  methods: {
    getItem () {
    //  subham url
      let uri = 'http://localhost:8090/employees/' + this.$route.params.id
      this.axios.get(uri).then((response) => {
        this.userdata = response.data
      })
    },
    update () {
      // subham url
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
