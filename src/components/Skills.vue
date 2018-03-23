<template>
  <div class="hello">
<div class="holder">
<form @submit.prevent="addSkill">

    <input type="text" placeholder="Enter a skill you have.." v-model="skill" v-validate="'min:5'" name="skill">

    <transition  name="alert-in" enter-active-class="animated zoomIn" leave-active-class="animated zoomOut">
      <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
    </transition>

  <ul>

<transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bouceOutDown" >
    <li v-for="(data , index) in skills" :key="index" >{{data.skill}}

      <i class="fas fa-minus-circle" v-on:click="remove(index)"></i>
       </li>
</transition-group>

  </ul>
  </form>
<p>These are the skills you posses</p>
</div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      skill: '',
      skills: [{ skill: 'Vue.js' }, { skill: 'Frontend Developer' }]
    };
  },
  methods: {
    addSkill() {
      this.$validator.validateAll().then(result => {
        if (result) {
          this.skills.push({ skill: this.skill });
          this.skill = '';
        } else {
          console.log('Not Valid');
        }
      });
    },
    remove(id) {
      this.skills.splice(id, 1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import 'https://cdn.jsdelivr.net/npm/animate.css@3.5.2/animate.min.css';

.holder {
  background: #fff;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul li {
  padding: 20px;
  font-size: 1.3em;
  background-color: rgb(172, 251, 222);
  border-left: 5px solid #61bd8d;
  margin-bottom: 2px;
  color: #3e5252;
}

p {
  text-align: center;
  padding: 30px 0;
  color: gray;
}

.container {
  box-shadow: 0px 0px 40px lightgray;
}
input {
  width: calc(100% - 40px);
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  background-color: #323333;
  color: #687f7f;
}
.alert {
  background: #fdf2ce;
  font-weight: bold;
  display: inline-block;
  padding: 5px;
  margin-top: -20px;
}

i {
  float: right;
}
</style>
