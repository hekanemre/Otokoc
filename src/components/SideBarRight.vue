<template>
  <div class="basket">
      <div @click="toggleDetail" class="sepet">{{symbol}} Detaylı Sepeti Göster</div>
      <div class="sepet-özeti">Sepet Özeti</div>
      <div class="products">
        <ul>
          <li v-show="eklendi1()" >Ford Focus Aks  <span class="sepetSonu">{{miktar_1}}  adet</span></li><br v-show="eklendi1()">
          <li v-show="eklendi2()" >Ford Focus Knuckle <span class="sepetSonu">{{miktar_2}}  adet</span></li><br v-show="eklendi2()">
          <li v-show="eklendi3()" >Ford Mondeo Aks <span class="sepetSonu">{{miktar_3}} adet</span></li><br v-show="eklendi3()">
          <li v-show="eklendi4()" >Ford Mondeo Knuckle <span class="sepetSonu">{{miktar_4}} adet</span></li><br v-show="eklendi4()">
          <li v-show="eklendi5()" >Volvo s40 Aks <span class="sepetSonu">{{miktar_5}} adet</span></li><br v-show="eklendi5()">
          <li v-show="eklendi6()" >Volvo s40 Knuckle <span class="sepetSonu">{{miktar_6}} adet</span> </li><br v-show="eklendi6()">
          <li v-show="eklendi7()" >Vovo s60 Aks <span class="sepetSonu">{{miktar_7}} adet</span></li><br v-show="eklendi7()">
          <li v-show="eklendi8()" >Volvo s60 Knuckle <span class="sepetSonu">{{miktar_8}} adet</span></li><br v-show="eklendi8()">
        </ul>
      </div>
      <button @click="removeAll" class="removeAll">Tüm Sepeti Boşalt</button>
  </div>
</template>

<script>

export default {
    name: "SideBarRight",
    props: ['miktar_1','miktar_2','miktar_3','miktar_4','miktar_5','miktar_6','miktar_7','miktar_8','toggleDetail','removeAll'],
    data () {
    return {
      quantity: 0,
      isVisibleBasket: true,
      symbol: '<<'
    }
  },
  methods: {  
    eklendi1(){
      if(this.miktar_1!=0 || this.miktar_1 != ''){
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
    }
  },
  components: {
  }     
}
</script>

<style>
.basket{
    width: 15%;
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
.sepetSonu{
  position: fixed;
  right: 10px;
}
.removeAll{
  cursor: pointer;
}
</style>