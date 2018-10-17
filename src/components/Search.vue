<template>
  <div>
    <h1>Search</h1>
              <form v-on:submit.prevent="search">
                <div class="col-md-10"></div>
          <div class="col-md-2">
            <router-link :to="{ name: 'CreateItem' }" class="btn btn-primary">Create employee</router-link>
          </div><br />
          <hr>
            <div class="row">
          <div class="col-md-4">
            <div class="form-group">
              <label>Search:</label>
              <input type="text" class="form-control  col-md-4" v-model="userdata.search" required />
            </div>
            </div>
            </div><br />
        <div class="form-group">
          <button class="btn btn-primary">Search</button>
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
    search () {
      // subhma url
      let uri = 'http://localhost:8090/employees/2'
      this.axios.get(uri, JSON.stringify(this.userdata), {
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
