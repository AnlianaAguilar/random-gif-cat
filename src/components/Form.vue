<template>
  <div>
    <div>
      <h1>Random Gif Cat</h1>
    </div>
    <div class="background_pink">
      <form>
        <label for="">Titulo: </label>
        <input type="text" v-model="title" /> <br />
        <label for="">Filtro: </label>
        <select @change="changeFilter">
          <option v-for="opt in filterOpt" :key="opt" :value="opt">
            {{ opt }}
          </option></select
        ><br />
        <div class="color">
          <label for="">Color: </label>
          <select v-model="color" @change="changeColor">
            <option
              v-for="color in colorOpt"
              :key="color.value"
              :value="color.value"
            >
              {{ color.value }}
            </option>
          </select>
          <div class="circule-color" :style="myStyles"></div>
        </div>
        <label for="">Tamaño: </label>
        <input type="text" v-model="size" />
      </form>
    </div>
    <div class="img-cat">
      <button @click="getCat">Obtener mi gatito</button>
      <div>
        <img :src="imagen" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Form-component",
  // props: {},
  data: function () {
    return {
      title: "",
      filter: "",
      color: "",
      size: "",
      imagen: "",
      filterOpt: ["", "blur", "mono", "sepia", "negative", "paint"],
      colorOpt: [
        {
          color: "Verde",
          value: "green",
        },
        {
          color: "Azul",
          value: "blue",
        },
        {
          color: "Rojo",
          value: "red",
        },
        {
          color: "Amarillo",
          value: "yellow",
        },
        {
          color: "Rosado",
          value: "pink",
        },
      ],
      myStyles: {
        backgroundColor: "",
      },
    };
  },
  computed: {
    img() {
      return `https://cataas.com/cat/says/${this.title}?size=${this.size}&color=${this.color}&filter=${this.filter}`;
    },
  },
  methods: {
    changeFilter(event) {
      this.filter = event.target.value;
      console.log(event.target.value);
    },

    changeColor(event) {
      this.myStyles.backgroundColor = event.target.value;
      console.log(event.target.value);
    },

    getCat() {
      this.imagen = `https://cataas.com/cat/says/${this.title}?size=${this.size}&color=${this.color}&filter=${this.filter}`;
      console.log(this.imagen);
      this.clean()
    },

    clean(){
      this.title=""
      this.filter=""
      this.color=""
      this.size=""
      this.myStyles.backgroundColor=""
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

.circule-color {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin: 0 10px;
}

.background_pink {
  background-color: pink;
  padding: 10px 0;
  width: 100%;
  margin: 10px -7px;
}

.color {
  padding: 2px 2px;
  display: flex;
  justify-content: center;
  margin-left: 50px;
}

select{
  width: 150px;
  height: 25px;
  margin: 5px 5px;
}

input{
  width: 150px;
  height: 25px;
  margin: 5px 5px;
}

.img-cat img{
  margin: 20px 20px;
}


</style>