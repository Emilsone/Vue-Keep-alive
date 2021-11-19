<template>
  <section>
    <div>
      <div class="fetch-profile">
        <button @click="fetchUsers" class="btn-users">Fetch Users</button>
        <h4 v-if="loading">Loading...</h4>
      </div>
      <div>
        <table class="user-table">
          <thead class="thead-bg">
            <tr>
              <th scope="col">#</th>
              <th scope="col">Name</th>
              <th scope="col">Username</th>
              <th scope="col">Email</th>
            </tr>
          </thead>
          <tbody v-for="(user, index) in users" :key="index">
            <tr>
              <th scope="row">{{ user.id }}</th>
              <td>{{ user.name }}</td>
              <td>{{ user.username }}</td>
              <td>{{ user.email }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </section>
</template>

<script>
import axios from 'axios';
export default {
  name: "GetPage",
  
  data() {
    return {
      users: [],
      loading: false,
    };
  },
  methods: {
    fetchUsers() {
      this.loading = true;
      this.users = [];

      axios
        .get("https://jsonplaceholder.typicode.com/users")
        .then((response) => {
          const data = response.data; // [{}, {}]
          this.users = data;
          this.loading = false;
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


.fetch-profile {
  display: flex;
  justify-content: center;
  width: 90%;
  padding: 30px;
}
.thead-bg {
  background-color: rgb(221, 220, 220);
}
.btn-users {
  background-color: #000;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}


.user-table{
  border-collapse: collapse;
  width: 100%;
}

.user-table td, .user-table th {
  border: 1px solid #ddd;
  padding: 8px;
}

.user-table tr:nth-child(even){background-color: #f2f2f2;}

.user-table tr:hover {background-color: #ddd;}

.user-table th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: rgb(221, 220, 220);
  color: rgb(49, 49, 49);
}

</style>
