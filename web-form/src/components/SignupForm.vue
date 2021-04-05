<template>
  <form @submit.prevent="handleSubmit">
    <label>Email:</label>
    <input type="email" required v-model="email" />

    <label>Password:</label>
    <input type="password" required v-model="password" />
    <div v-if="passWordError" class="error">{{ passWordError }}</div>

    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web developer</option>
      <option value="designer">Web designer</option>
    </select>

    <br />

    <label>Skills:</label>

    <div>
      <input type="checkbox" value="checkFirst" v-model="names" />
      <label>HTML</label>
    </div>
    <div>
      <input type="checkbox" value="checkSecond" v-model="names" />
      <label>CSS</label>
    </div>
    <div>
      <input type="checkbox" value="checkThird" v-model="names" />
      <label>Vue</label>
    </div>
    <label>other skills:</label>
    <input type="text" v-model="tempSkill" @keyup.space.="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="removeSkill(skill)">{{ skill }}</span>
      <button type="button" class="removeSkillBtn" @click="removeSkill(skill)">
        &#10060;
      </button>
    </div>
    <br />
    <input type="checkbox" v-model="terms" required />
    <label>Accept terms and conditions</label>

    <div class="submitWrapperBtn">
      <button class="submitFormBtn" type="submit">Create an account</button>
    </div>
  </form>
  <p>{{ terms }}</p>
  <p>{{ names }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "designer",
      terms: false,
      names: [],
      tempSkill: "",
      skills: [],
      passWordError: "",
    };
  },
  methods: {
    addSkill(e) {
      console.log(e);
      if (this.tempSkill) {
        this.skills = this.skills.filter((skill) => skill !== this.tempSkill);

        this.skills.push(this.tempSkill);
        this.tempSkill = "";
      }
    },
    removeSkill(skill) {
      let ans = confirm(
        "Are you sure you want to remove " + "'" + skill + "' ?"
      );
      if (ans) {
        this.skills = this.skills.filter((skillTmp) => {
          return skillTmp !== skill;
        });
      }
    },
    handleSubmit() {
      console.log("asd");
      this.passWordError =
        this.password.length > 5
          ? ""
          : "Password must be atleast 6 chars/numbers long";
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
  border-radius: 20px;
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
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background-color: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
}
.removeSkillBtn {
  cursor: pointer;
  margin-left: 0px;
  padding: 0 0 0 3px;
  border: none;
  font-weight: bold;
  background-color: inherit;
  color: #777;
  text-align: center;
}
.removeSkillBtn:focus {
  outline: 0;
}
.submitWrapperBtn {
  text-align: center;
}
.submitFormBtn {
  border-radius: 10px;
  background-color: rgb(11, 132, 245);
  border: 1px solid black;
  color: white;
}
.error {
  font-size: 0.7em;
  color: red;
  font-weight: bold;
  padding: 4px 0;
}
.someOp {
  border-bottom: 1px solid #ddd;
}
</style>