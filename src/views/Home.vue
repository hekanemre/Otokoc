<template>
  <div class="home container">
    <div class="header flex">
      <div class="parts flex flex-column">
        <div class="left flex">
          <div @click="toggleFilterBranch" class="branch-filter" ref="filter">
            <span>Marka</span>
            <img src="@/assets/arrow-down.svg" alt="">
            <ul v-if="filterBranch" class="filter-branch">
              <li @click="toggleFord">Ford</li>
              <li @click="toggleVolvo">Volvo</li>
            </ul>
          </div>
        </div>
        <div class="center flex">
            <span>Model</span>
            <img src="@/assets/arrow-down.svg" alt="">
            <ul v-if="filterModel1" class="filter-model1">
              <li @click="focusPart">Focus</li>
              <li @click="mondeoPart">Mondeo</li>
            </ul>
            <ul v-if="filterModel2" class="filter-model2">
              <li @click="s40Part">s40</li>
              <li @click="s60Part">s60</li>
            </ul>
        </div>
        <div class="right flex">
          Parça Numarası <br>
          <input type="number" min="0" max="8" @click="searchPart" @keyup.enter="findPart" v-model="partValue">
          <br>
          <button class="tüm-parçalar" @click="toggleAll">Tüm Parçalar</button>
        </div>
      </div>
    </div>
    <div class="subtitle">
      <div class="image">Resim</div>
      <div class="part-number">Parça Numarası</div>
      <div class="name">Parça Adı</div>
      <div class="cost">Tutar</div>
      <div class="quantity">Miktar</div>
    </div>
    <div v-if="isVisibleFocus" class="parca-1">
        <div class="resim">Resim</div>
        <div class="numara">1</div>
        <div class="ad">Focus Aks</div>
        <div class="tutar">100 ₺</div>
        <div class="miktar">
        <input class="1" type="number" min="0" v-model="input1">
        <button @click="sepet1" class="add">Sepete Ekle</button>
        </div>
    </div>
    <div v-if="isVisibleFocus1" class="parca-2">
        <div class="resim1">Resim</div>
        <div class="numara1">2</div>
        <div class="ad1">Focus Knuckle</div>
        <div class="tutar1">150 ₺</div>
        <div class="miktar1">
        <input class="2" type="number" min="0" v-model="input2">
        <button @click="sepet2" class="add1">Sepete Ekle</button>
        </div>
    </div> 
    <div v-if="isVisibleMondeo" class="parca-1">
        <div class="resim2">Resim</div>
        <div class="numara2">3</div>
        <div class="ad2">Mondeo Aks</div>
        <div class="tutar2">200 ₺</div>
        <div class="miktar2">
        <input class="3" type="number" min="0" v-model="input3">
        <button @click="sepet3" class="add2">Sepete Ekle</button>
        </div>
    </div>
    <div v-if="isVisibleMondeo1" class="parca-2">
        <div class="resim3">Resim</div>
        <div class="numara3">4</div>
        <div class="ad3">Mondeo Knuckle</div>
        <div class="tutar3">250 ₺</div>
        <div class="miktar3">
        <input class="4" type="number" min="0" v-model="input4">
        <button @click="sepet4" class="add3">Sepete Ekle</button>
        </div>
    </div>
    <div v-if="isVisibles40" class="parca-1">
        <div class="resim4">Resim</div>
        <div class="numara4">5</div>
        <div class="ad4">s40 Aks</div>
        <div class="tutar4">300 ₺</div>
        <div class="miktar4">
        <input class="5" type="number" min="0" v-model="input5">
        <button @click="sepet5" class="add4">Sepete Ekle</button>
        </div>
    </div>
    <div v-if="isVisibles401" class="parca-2">
        <div class="resim5">Resim</div>
        <div class="numara5">6</div>
        <div class="ad5">s40 Knuckle</div>
        <div class="tutar5">350 ₺</div>
        <div class="miktar5">
        <input class="6" type="number" min="0" v-model="input6">
        <button @click="sepet6" class="add5">Sepete Ekle</button>
        </div>
    </div>
    <div v-if="isVisibles60" class="parca-1">
        <div class="resim6">Resim</div>
        <div class="numara6">7</div>
        <div class="ad6">s60 Aks</div>
        <div class="tutar6">400 ₺</div>
        <div class="miktar6">
        <input class="7" type="number" min="0" v-model="input7">
        <button @click="sepet7" class="add6">Sepete Ekle</button>
        </div>
    </div>
    <div v-if="isVisibles601" class="parca-2">
        <div class="resim7">Resim</div>
        <div class="numara7">8</div>
        <div class="ad7">s60 Knuckle</div>
        <div class="tutar7">450 ₺</div>
        <div class="miktar7">
        <input class="8"  type="number" min="0" v-model="input8">
        <button @click="sepet8" class="add7">Sepete Ekle</button>
        </div>
    </div>
  </div>
  <SideBarRight 
  v-if="showSideBarRight"
  :toggleDetail="toggleSideBar"
  :miktar_1="value1" 
  :miktar_2="value2"
  :miktar_3 ="value3"
  :miktar_4 ="value4"
  :miktar_5 ="value5"
  :miktar_6 ="value6"
  :miktar_7 ="value7"
  :miktar_8 ="value8"
  :removeAll="removeItems"
  />
  <SideBar
  v-if="showSidebar"
  :miktar_1 ="value1"
  :miktar_2="value2"
  :miktar_3 ="value3"
  :miktar_4 ="value4"
  :miktar_5 ="value5"
  :miktar_6 ="value6"
  :miktar_7 ="value7"
  :miktar_8 ="value8"
  :toggleSummary="toggleSideBarRight"/>
</template>

<script>
import SideBarRight from '@/components/SideBarRight.vue'
import SideBar from '@/components/SideBar.vue'

export default {
  name: "Home",
  data: ()=>{
    return {
      filterBranch: false,
      filterModel1: false,
      filterModel2: false,
      isVisibleFocus: true,
      isVisibleFocus1: true,
      isVisibleMondeo: true,
      isVisibleMondeo1: true,
      isVisibles40: true,
      isVisibles401: true,
      isVisibles60: true,
      isVisibles601: true,
      partValue:'',
      value1:'',
      value2:'',
      value3:'',
      value4:'',
      value5:'',
      value6:'',
      value7:'',
      value8:'',
      input1:'',
      input2:'',
      input3:'',
      input4:'',
      input5:'',
      input6:'',
      input7:'',
      input8:'',
      showSideBarRight: true,
      showSidebar: false
    }

  },
  methods: {toggleFilterBranch(){
      this.filterBranch = true
      this.isVisibleFocus= false
      this.isVisibleFocus1= false
      this.isVisibleMondeo= false
      this.isVisibleMondeo1= false
      this.isVisibles40= false
      this.isVisibles401= false
      this.isVisibles60= false
      this.isVisibles601= false
    },
    toggleAll(){
      this.isVisibleFocus= true
      this.isVisibleFocus1= true
      this.isVisibleMondeo= true
      this.isVisibleMondeo1= true
      this.isVisibles40= true
      this.isVisibles401= true
      this.isVisibles60= true
      this.isVisibles601= true
    },
      toggleFord(){
        this.filterModel1 =true 
        this.filterModel2 =false 
      },
      toggleVolvo(){
        this.filterModel2 =true
        this.filterModel1 =false
      },
      focusPart(){
        this.filterBranch = false
        this.filterModel1= false
        this.isVisibleFocus= true
        this.isVisibleFocus1= true
      },
      mondeoPart(){
        this.filterBranch = false
        this.filterModel1= false
        this.isVisibleMondeo= true
        this.isVisibleMondeo1= true
      },
      s40Part(){
        this.filterBranch = false
        this.filterModel2= false
        this.isVisibles40= true
        this.isVisibles401= true
      },
      s60Part(){
        this.filterBranch = false
        this.filterModel2= false
        this.isVisibles60= true
        this.isVisibles601= true
      },
      sepet1 (){
        this.value1 = this.input1
      },      
      sepet2 (){
        this.value2 = this.input2
      },
      sepet3 (){
        this.value3 = this.input3
      },
      sepet4 (){
        this.value4 = this.input4
      },
      sepet5 (){
        this.value5 = this.input5
      },
      sepet6 (){
        this.value6 = this.input6
      },
      sepet7 (){
        this.value7 = this.input7
      },
      sepet8 (){
        this.value8 = this.input8
      },
      toggleSideBar(){
        this.showSideBarRight = !this.showSideBarRight
        this.showSidebar = !this.showSidebar
      },
      toggleSideBarRight(){
        this.showSidebar = !this.showSidebar    
        this.showSideBarRight = !this.showSideBarRight
      },
      removeItems(){
        this.value1 = 0
        this.value2 = 0
        this.value3 = 0
        this.value4 = 0
        this.value5 = 0
        this.value6 = 0
        this.value7 = 0
        this.value8 = 0
      },
      findPart(){
        if (this.partValue=='1'){
          this.isVisibleFocus=true
          this.isVisibleFocus1=false
          this.isVisibleMondeo= false
          this.isVisibleMondeo1= false
          this.isVisibles40= false
          this.isVisibles401= false
          this.isVisibles60= false
          this.isVisibles601= false
        }else if(this.partValue=='2'){
          this.isVisibleFocus=false
          this.isVisibleFocus1=true
          this.isVisibleMondeo= false
          this.isVisibleMondeo1= false
          this.isVisibles40= false
          this.isVisibles401= false
          this.isVisibles60= false
          this.isVisibles601= false 
        }else if(this.partValue=='3'){
          this.isVisibleFocus=false
          this.isVisibleFocus1= false
          this.isVisibleMondeo= true
          this.isVisibleMondeo1= false
          this.isVisibles40= false
          this.isVisibles401= false
          this.isVisibles60= false
          this.isVisibles601= false
        }else if(this.partValue=='4'){
          this.isVisibleFocus=false
          this.isVisibleFocus1= false
          this.isVisibleMondeo= false
          this.isVisibleMondeo1= true
          this.isVisibles40= false
          this.isVisibles401= false
          this.isVisibles60= false
          this.isVisibles601= false
        }else if(this.partValue=='5'){
          this.isVisibleFocus=false
          this.isVisibleFocus1= false
          this.isVisibleMondeo= false
          this.isVisibleMondeo1= false
          this.isVisibles40= true
          this.isVisibles401= false
          this.isVisibles60= false
          this.isVisibles601= false
        }else if(this.partValue=='6'){
          this.isVisibleFocus=false
          this.isVisibleFocus1= false
          this.isVisibleMondeo= false
          this.isVisibleMondeo1= false
          this.isVisibles40= false
          this.isVisibles401= true
          this.isVisibles60= false
          this.isVisibles601= false
        }else if(this.partValue=='7'){
          this.isVisibleFocus=false
          this.isVisibleFocus1= false
          this.isVisibleMondeo= false
          this.isVisibleMondeo1= false
          this.isVisibles40= false
          this.isVisibles401= false
          this.isVisibles60= true
          this.isVisibles601= false
        }else if(this.partValue=='8'){
          this.isVisibleFocus=false
          this.isVisibleFocus1= false
          this.isVisibleMondeo= false
          this.isVisibleMondeo1= false
          this.isVisibles40= false
          this.isVisibles401= false
          this.isVisibles60= false
          this.isVisibles601= true
        }
      }
  },
  components: {
    SideBarRight,
    SideBar
  },
};
</script>

<style scoped>
.home{
  margin: 0;
  width: 80%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  color:white;
}
.image,
.part-number,
.name,
.cost,
.quantity{
  width: 20%;
  text-align: center;
}
.parca-1,
.parca-2{
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  background-color: #A7B1B4;
  color: black;
  width: 100%;
  margin: 5px;
  height: 60px;
  border-radius: 3px;
  text-align: center;
}
input{
  width: 40%;
  background-color: white;
}
.subtitle{
  width: 100%;
  display: flex;
  justify-content: space-between;
  flex-direction: row;
  color:black;
  font-weight: bold;
  margin: 5px;
  border-radius: 3px;
  background-color: #D5EEF6;
  flex: 1;
  border-radius: 5px;
}

.header{
  width: 75%;
  margin-bottom: 65px;
}

.parts{
  display: flex;
  justify-content: space-between;
}

.left,
.center{
  text-align: center;
  background-color: white;
  color: black;
  margin: 10px;
  flex: 1;
}
.right{
  margin: 5px;
  flex: 1;
  text-align: center;
  color: black;
}
span{
  font-size: 16px;
}
span:hover{
  cursor: pointer;
}
.filter{
  align-items: center;
  border-radius: 5px;
  background-color: white;
}
.filter:hover{
  cursor: pointer;
}
li{
  cursor: pointer;
  font-size: 12px;
  padding: 10px;
  background-color: white;
  color: black;
  text-align: center;
}
li:hover{
  color: white;
  background-color: #1e2139;
}
.resim,.numara,.ad,.tutar,.miktar,
.resim1,.numara1,.ad1,.tutar1,.miktar1,
.resim2,.numara2,.ad2,.tutar2,.miktar2,
.resim3,.numara3,.ad3,.tutar3,.miktar3,
.resim4,.numara4,.ad4,.tutar4,.miktar4,
.resim5,.numara5,.ad5,.tutar5,.miktar5,
.resim6,.numara6,.ad6,.tutar6,.miktar6,
.resim7,.numara7,.ad7,.tutar7,.miktar7
{
  width: 20%;
  text-align: center;
  margin-top: 1.5%;
}
.tüm-parçalar{
  margin-top: 5px;
}
button{
  cursor: pointer;
}
</style>