<template>
  <form action="#">
    <label>Email:</label>
    <input type="email" required v-model="email">

    <label>Password:</label>
    <input type="password" required v-model="password">
 
    <label>Role</label>
    <select v-model="role">
      <option value="f-developer">Frontend Developer</option>
      <option value="b-developer">Backend Developer</option>
    </select> 

    <label>Skills</label>
    <input type="text" v-model="tempSkills" @keyup="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill">
      {{ skill }}
    </div>

    <div class="terms">
      <input type="checkbox" v-model="terms" required>
      <label>Accept terms and conditions</label>
    </div>
</form>

  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms: {{ terms }}</p>
  <p>Names: {{ names }}</p>
  <p>Skills: {{ skills }}</p>
</template>

<script>

export default {
  data(){
    return{
      email: 'mario',
      password: '',
      role: 'f-developer',
      terms: false,
      names: [],
      tempSkills: '',
      skills: []
    }
  },
  methods: {
    addSkill(e){
      if(e.key === ',' && this.tempSkills){
        if(!this.skills.includes(this.tempSkills)) {
            this.skills.push(this.tempSkills)
      }
      this.tempSkills = ''
    }
    }
  }
}
</script>

<style>
  form {
    max-width:420px;
    margin: 30px auto;
    background-color: #a2bae8;
    text-align:left;
    padding: 40px;
    border-radius: 10px;
  }
  label {
    color: grey;
    display: inline-block;
    margin:25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
  }
  input, select{
    display:block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border-bottom: 1px solid #dddddd60;
    color: #555;
    border:none;
  }
  input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
  }
</style>