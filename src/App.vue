<template>
  <h1>Technical Skills</h1>
  <ul>
    <li v-for="(skill, index) in skills" :key="skill.name">
       <div> {{ skill.name }} <button v-on:click="removeSkill(index)"> X </button> </div>
    </li>
  </ul>
  <form 
      @submit.prevent="addSkill">
    <input v-model="newSkill" placeholder="Type Skill">
    <button type="submit">Add Skill</button>
  </form>
  <h3>Total Skills in the list is {{skillsCount}}</h3>
 
</template>

<script>
export default {
  computed: {
    skillsCount() {
      return this.skills.length;
    },
    
  },
  methods: {
    addSkill() {
      if(this.newSkill != "") {
       // this.skills.push({ name: this.newSkill});
        this.skills.unshift({ name: this.newSkill});
        this.newSkill = ''; // not entery empty value
      }
    },
    removeSkill(index) {
      this.skills = this.skills.filter((skill, i) => i != index);
    },
  },
  data() {
    return {      
      newSkill: "",
      skills: [
        { name: "PHP" },
        { name: "JAVA" },
        { name: "Python" },
        { name: "HTML" },
        { name: "Javascript" },
      ],      
    }
  }
}
</script>

<style>

</style>