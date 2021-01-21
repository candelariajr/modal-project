<!--Removing Boilerplate-->
<template>
  <!--
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  -->
  <h1>{{ title}}</h1><br><br>
  <input type="text" ref="name"><br><br>
  <button @click="handleClick">CLICK</button>
  <hr>
  <!-- Invoke the Modal component -->
  <!-- <Modal header="Sign up for The Thing" text="Get some free ninja swag!"/> -->
  <!-- Replace it with proper data binding -->
  <p>Welcome...</p>
  <div v-if="showModal">
    <Modal :theme="theme" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign Up Now!</a>
        <a href="#">Click here for more info</a>
      </template>
      <h1>Ninja Giveaway!</h1>
      <p>Get your ninja swag!</p>
    </Modal>
  </div>
  <div v-if="showModal2">
    <Modal :theme="theme" @close="toggleModal2">
      <h1>Modal 2 Header!</h1>
      <template v-slot:links>
        {{modal2text}}
      </template>
    </Modal>
  </div>
  <button @click="toggleModal">Open Modal</button><br><br>
  <button @click="toggleModal2">Open Modal2</button>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue';
import Modal from './components/Modal';

export default {
  name: 'App',
  components: {Modal},
  data(){
    return{
      title: "First Vue CLI App",
      header: 'Sign up for The Thing',
      text: 'Get some free ninja swag!',
      showModal: false,
      theme: 'nosale',
      showModal2: false,
      modal2text: "This is Modal 2"
    }
  },
  methods: {
    handleClick(){
      //refs get the ref ELEMENT
      //alert(this.$refs.name);
      this.$refs.name.classList.add('active');
      this.$refs.name.focus();
    },
    toggleModal(){
      this.showModal = !this.showModal;
    },
    toggleModal2(){
      this.showModal2 = !this.showModal2;
    }
  }
}
</script>

<style>
*{
  user-select: none;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}

.active{
  background-color:cyan;
}

</style>
