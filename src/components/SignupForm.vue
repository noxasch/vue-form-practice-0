<script setup>
  import { ref, onUpdated } from 'vue';

  const email = ref('');
  const password = ref('');
  const role = ref('');
  const terms = ref(false);
  const tempSkill = ref('');
  const skills = ref([]);
  // const names = ref([]);

  function addSkill() {
    if (!skills.value.includes(tempSkill.value)) {
      skills.value.push(tempSkill.value);
    }
    
    tempSkill.value = '';
  }

  function deleteSkill(skill) {
    skills.value = skills.value.filter((item) => item != skill);
  }
</script>

<template>
  <form action="">
    <label for="email">Email</label>
    <input name="email" type="email" required v-model="email">

    <label for="password">Password</label>
    <input name="password" type="password" required v-model="password">

    <label for="role">Role</label>
    <select name="role" id="" v-model="role" >
      <option value="" disabled>Select role</option>
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <label for="skills">skills:</label>
    <input type="text" v-model="tempSkill" @keyup.enter="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>

    <div class="terms">
      <input type="checkbox" name="tos" required v-model="terms">
      <label for="tos">Accept terms and conditions</label>
    </div>

    <!-- <div>
      <input type="checkbox" value="shaun" v-model="names">
      <label>Shaun</label>
    </div>
    <div>
      <input type="checkbox" value="yoshi" v-model="names">
      <label>Yoshi</label>
    </div>
    <div>
      <input type="checkbox" value="mario" v-model="names">
      <label>Mario</label>
    </div> -->
  </form>
</template>

<style scoped>
  form {
    max-width: 420px;
    margin: 30px auto;
    background: #fff;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
  }

  label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
  }

  input, select {
    display: block;
    background: #fff;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
  }

  input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
  }

  .pill {
    display: inline-block;
    margin: 20px 10px 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
  }
</style>
