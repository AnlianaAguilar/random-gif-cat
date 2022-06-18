<template>
  <div>
    <div>
      <h1>Random Gif Cat</h1>
    </div>
    <div :class={background_pink}>
      <form>
        <label for="">Titulo</label>
        <input type="text" v-model="title" /> <br />
        <label for="">Filtro</label>
        <select @change="changeFilter">
          <option 
          v-for="opt in filterOpt" 
          :key="opt"
          :value="opt">
            {{opt}}
          </option>
          </select><br/>
        <label for="">Color</label>
        <select v-model="color" @change="changeColor">
          <option 
          v-for="color in colorOpt" 
          :key="color.value"
          :value="color.value">
            {{color.value}}
          </option>
        </select>
        <div class="circule-color" :style="myStyles"></div><br />
        <label for="">Tamaño</label>
        <input type="text" v-model="size"/>
      </form>
    </div>
    <div>     
      <button @click="getCat">Obtener mi gatito</button>
      <img :src="imagen" alt="">
    </div>
  </div>
</template>

<script>
export default {
  name: "Form-component",
  // props: {},
  data: function () {
    return {
      title: '',
      filter: '',
      color: '',
      size: '',
      imagen:'',
      filterOpt:[
        '',
        'blur',
        'mono',
        'sepia',
        'negative',
        'paint',
      ],
      colorOpt:[
        {
          color:'Verde',
          value:'green'
        },
        {
          color:'Azul',
          value:'blue'
        },
        {
          color:'Rojo',
          value:'red'
        },
        {
          color:'Amarillo',
          value:'yellow'
        },
        {
          color:'Rosado',
          value:'pink'
        },
      ],
      myStyles:{
        backgroundColor: '',
      }
    };
  },
  computed: {
    img(){
      return `https://cataas.com/cat/says/${this.title}?size=${this.size}&color=${this.color}&filter=${this.filter}`
    }
  },
  methods: {
    changeFilter(event){
      this.filter = event.target.value;
      console.log(event.target.value)
    },

    changeColor(event){
      this.myStyles.backgroundColor = event.target.value;
      console.log(event.target.value)
    },
  
    getCat(){
      this.imagen= `https://cataas.com/cat/says/${this.title}?size=${this.size}&color=${this.color}&filter=${this.filter}`
      console.log(this.imagen)
    }
    
  },
  // watch: {},
  // components: {},
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
};
</script>

<style scoped>
  .circule-color{
    width: 30px;
    height: 30px;
    border-radius: 50%;
  }

  .background_pink{
    background-color: palevioletred
  }
</style>