<script>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
export default{
  data(){
    return{
      nama: ""
    }
  },
  methods:{
    berubah(){
      this.nama = "daffa"
    },
    async ambildata(){
      const response = await fetch("http://localhost:8989/sensor3");
      const data = await response.json();
      this.nama = data.sensor3
      console.log(data)
    },
  },
};
</script>

<template>
  <header>
    <input type="text" v-model="nama"/>
    {{ nama }}
    <button @click="berubah()">berubah</button>
    <button @click="ambildata()">ambildata</button>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="Mencoba Vue" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>
