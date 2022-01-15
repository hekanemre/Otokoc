<template>
  <div class="basket">
      <div @click="toggle" class="sepet">{{symbol}} Detaylı Sepeti Göster</div>
      <div class="sepet-özeti">Sepet Özeti</div>
      <div class="products">
        <ul>
          <li v-show="eklendi1()" >Ford Focus...{{miktar_1}}  adet Tutarı:{{miktar_1*100}} ₺</li><br v-show="eklendi1()">
          <li v-show="eklendi2()" >Ford Focus...{{miktar_2}}  adet Tutarı:{{miktar_2*150}} ₺</li><br v-show="eklendi2()">
          <li v-show="eklendi3()" >Ford Monde...{{miktar_3}} adet Tutarı:{{miktar_3*200}} ₺</li><br v-show="eklendi3()">
          <li v-show="eklendi4()" >Ford Monde...{{miktar_4}} adet Tutarı:{{miktar_4*250}} ₺</li><br v-show="eklendi4()">
          <li v-show="eklendi5()" >Volvo s40...{{miktar_5}} adet Tutarı:{{miktar_5*300}} ₺</li><br v-show="eklendi5()">
          <li v-show="eklendi6()" >Volvo s40...{{miktar_6}} adet Tutarı:{{miktar_6*350}}₺ </li><br v-show="eklendi6()">
          <li v-show="eklendi7()" >Vovo s60...{{miktar_7}} adet Tutarı:{{miktar_7*400}} ₺</li><br v-show="eklendi7()">
          <li v-show="eklendi8()" >Volvo s60...{{miktar_8}} adet Tutarı:{{miktar_8*450}} ₺</li><br v-show="eklendi8()">
        </ul>
      </div>
  </div>
  <SideBar
  v-if="showSidebar"/>
</template>

<script>
import SideBar from '@/components/SideBar.vue'
export default {
    name: "SideBarRight",
    props: ['miktar_1','miktar_2','miktar_3','miktar_4','miktar_5','miktar_6','miktar_7','miktar_8'],
    data () {
    return {
      showSidebar: false,
      quantity: 0,
      isVisibleBasket: true,
      symbol: '<<'
    }
  },
  methods: {
    eklendi1(){
      if(this.miktar_1!=0){
        return true
      }
    },
    eklendi2(){
      if(this.miktar_2!=0){
        return true
      }
    },
    eklendi3(){
      if(this.miktar_3!=0){
        return true
      }
    },
    eklendi4(){
      if(this.miktar_4!=0){
        return true
      }
    },
    eklendi5(){
      if(this.miktar_5!=0){
        return true
      }
    },
    eklendi6(){
      if(this.miktar_6!=0){
        return true
      }
    },
    eklendi7(){
      if(this.miktar_7!=0){
        return true
      }
    },
    eklendi8(){
      if(this.miktar_8 != 0){
        return true
      }
    },
    toggle(){
      this.showSidebar = !this.showSidebar
    }
  },
  components: {
    SideBar
  }     
}
</script>

<style>
.basket{
    width: 15%;
    height: 850px;
    position: fixed;
    background-color: white;
    text-align: center;
    color: black;
    bottom: 0;
    right: 0;
    top: 86.4px;
    bottom: 0;
    border-left: 2px solid  black;
    border-top: 2px solid  black;
}
.sepet{
  margin: 10px;
  cursor: pointer;
}
.sepet-özeti{
  margin: 30px;
  font-weight: bold;
}
li{
  text-align: left;}
  
ul {
  list-style-type: none;
}

</style>