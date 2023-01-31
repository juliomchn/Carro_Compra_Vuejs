<template>
  <div id="app">
    
    <div class="container">

      <div class="row row-cols-3">
          <div class="col" v-for="i in productos" :key="i.id">
            <producto :producto="i" v-on:agregar-carro="agregarProdCarro" :estaEnCarro="estaEnCarro(i)"></producto>
          </div>
          <div class="col">
            <carro :items="carro" v-on:removeItem="removeItem"> </carro>
          </div>
      </div>
      
    </div>
    
  </div>
</template>

<script>

import Producto from './components/Producto.vue'
import Carro from './components/Carro.vue'
import productos from '../productos.json'
export default {
  name: 'App',
  components: {
    Producto,
    Carro
  },
  data(){
    return{
      productos,
      carro:[]
    }
  },
  methods:{
    agregarProdCarro(producto){
      this.carro.push(producto);
    },
    estaEnCarro(producto){
      const item = this.carro.find(item => item.id === producto.id);
      if(item){
        return true;
      }else{
        return false;
      }
    },
    removeItem(producto){
      this.carro = this.carro.filter(item => item.id != producto.id)
    }
  }
}
</script>
    

<style>

</style>
