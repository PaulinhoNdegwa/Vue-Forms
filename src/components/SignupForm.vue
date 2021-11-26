<template>
  <form>
    <h3>Signup Form</h3>
    <label>Email: </label>
    <input
      type="email"
      v-model="email"
      placeholder="Enter a valid email"
      required
    />

    <label>Password: </label>
    <input
      type="password"
      v-model="password"
      placeholder="Enter a password"
      required
    />

    <label>Role: </label>
    <select v-model="role">
      <option :value="''" disabled>Select a role</option>
      <option value="developer">Web developer</option>
      <option value="designer">Web designer</option>
    </select>

    <label>Skills: </label>
    <input
      type="text"
      v-model="tempSkill"
      @keyup.enter.prevent="saveSkill"
      placeholder="Type skill name then press Enter (Click skill to remove)"
    />
    <span v-for="skill in skills" :key="skill" @click="removeSkill(skill)">
      {{ skill }}
    </span>
    <div class="terms">
      <input type="checkbox" v-model="terms" required />
      <label>Agree terms and conditions</label>
    </div>
    <a @click="submit">Create an account</a>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      terms: false,
      tempSkill: "",
      skills: [],
    };
  },
  methods: {
    saveSkill(e) {
      if (this.tempSkill) {
        this.skills.push(e.target.value);
      }
      this.tempSkill = "";
    },
    removeSkill(skill) {
      this.skills = this.skills.filter((item) => item != skill);
    },
    submit(e) {
      alert("Thank you for signing up " + this.email);
    },
  },
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
form h3 {
  text-align: center;
  text-decoration: underline;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
  outline: none;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
form span {
  display: inline-block;
  background: rgb(195, 195, 195);
  color: rgb(105, 105, 105);
  padding: 3px 10px;
  margin: 4px 3px;
  border-radius: 3px;
  font-size: 14px;
  font-weight: 700;
  font-style: italic;
  cursor: pointer;
}
form a {
  display: inline-block;
  background: rgb(98, 1, 167);
  padding: 7px 15px;
  color: white;
  border-radius: 3px;
  margin: 5px auto;
  font-weight: 600;
}
</style>