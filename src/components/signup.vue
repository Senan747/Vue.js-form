<template>
  <form @submit="handleSubmit()">
    <label>Email:</label>
    <input type="email" required v-model="email">

    <label>Password:</label>
    <input type="password" required v-model="password">
    <div v-if="passwordError" class="error">!{{ passwordError }}</div>
 
    <label>Role</label>
    <select v-model="role">
      <option value="f-developer">Frontend Developer</option>
      <option value="b-developer">Backend Developer</option>
    </select> 

    <label>Skills</label>
    <input type="text" v-model="tempSkills" @keyup="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span> 
    </div>

    <div class="terms">
      <input type="checkbox" v-model="terms" required>
      <label>Accept terms and conditions</label>
    </div>

    <div class="submit">
      <button>Create account</button>
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
      email: '',
      password: '',
      role: '',
      terms: false,
      names: [],
      tempSkills: '',
      skills: [],
      passwordError: ''
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
    },
    deleteSkill(skill){
      this.skills = this.skills.filter((item) => {
        return skill !== item 
      })
    },
    handleSubmit(){
      this.passwordError = this.password.length > 6 ? '' : 'Password must be at least 6 chars long'
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
    font-size: 0.8em;
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
  .pill{
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background-color: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
  }
  button{
    border:none;
    background-color: #49959e;
    color:white;
    padding: 10px 20px;
    font-size: 16px;
    border-radius: 7px;
  }
  .submit{
    text-align: center;
  }
  .error{
    color:red;
    font-size:16px;
    margin-top: 5px;
    font-weight: 600; 
  }
</style>