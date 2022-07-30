<template>
  <div class="hello">
    <form @submit="onSubmit()">
      <label>{{ mail }}</label>
      <input v-model="email" name="email" placeholder="Email" type="email" />
      <label>{{ passwor }}</label>
      <input
        v-model="password"
        name="password"
        placeholder="Password"
        type="password"
      />

      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
const userdata = [];
export default {
  name: 'HelloWorld',
  data() {
    return {
      email: '',
      password: '',
    };
  },
  props: ['mail', 'passwor'],
  methods: {
    onSubmit() {
      const Simpledb = require('simpl.db');
      const db = new Simpledb();
      const usercollection = db.createCollection('userrdata');
      const newuser = {
        id: Math.floor(Math.random() * 100000),
        email: this.email,
        password: this.password,
      };
      userdata.push(newuser);
      this.email = '';
      this.password = '';
      usercollection.createBulk(userdata);
    },
  },
};
</script>
<style>
.hello {
  text-align: center;
  margin: 20px;
  display: inline-block;
  box-sizing: border-box;
}
input {
  display: inline-block;
  margin: 18px;
}
</style>
