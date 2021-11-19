<template>
  <section>
    <div>
      <form class="input-feild" @submit.prevent="handleSubmit">
        <input
          class="search-input"
          type="text"
          placeholder="Name"
          v-model="name"
        />
        <input
          class="search-input"
          v-model="userName"
          placeholder="Username"
          type="text"
        />
        <input
          class="search-input"
          v-model="email"
          placeholder="Email"
          type="text"
        />
        <button class="btn-search">Add Employee</button>
      </form>
        <p v-if="submitting">Submitting...</p>
        <p v-if="loading">Loading...</p>
    </div>
  </section>
</template>

<script>
import axios from "axios";
export default {
  name: "PostPage",

  data() {
    return {
      users: [],
      loading: false,
      submitting: false,
      name: "",
      userName: "",
      email: "",
    };
  },
  methods: {
    handleSubmit() {
      this.submitting = true;
      axios
        .post("https://jsonplaceholder.typicode.com/users", {
          name: this.name,
          username: this.userName,
          email: this.email,
        })
        .then((response) => {
          const data = response.data;
          this.users.push(data);
          this.name = "";
          this.userName = "";
          this.email = "";
          this.submitting = false;
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.search-input {
  padding: 6px;
  border: 2px solid black;
  margin-top: 8px;
  margin-right: 16px;
  font-size: 19px;
  width: 20%;
  color: black;
}
.input-feild {
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin: 10px 0px;
}
.btn-search {
  background-color: #000;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}
</style>
