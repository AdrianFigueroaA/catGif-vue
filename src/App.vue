<template>
  <div class="seccion">
        <div class="titulo">
          <h1>Random Gift Cat</h1>
          <h2>complete todas las opciones para pedir su Gif!</h2>
        </div>

        <div id="main" >
          <div  id="labels">
          <div> 
            <label>Titulo : </label><input type="text" v-model="title" placeholder="Ingresa una Palabra" />
          </div> 

          <div>
            <label>Color : </label>
            <select v-model="colorSelected">
              <option selected disabled value="color"
                >--Seleccione un Color--</option
              >

              <option v-for="(color, i) in colores" :key="i" :value="color">
                <p>{{ colorTraducidos[color] }}</p>
              </option>
            
            </select>
            <div class="imagen" :style="{ backgroundColor: colorSelected }"></div>
          </div> 

          <div> 
            <label>Filtros : </label>
            <select v-model="filtroSelected">
              <option disabled selected value="filtro"
                >--Seleccione un filtro--</option>

              <option v-for="(filtro, i) in filtros" :key="i" :value="filtro">
                <p>{{ filtro }}</p>
              </option>
            </select>
          </div>

          <div>
          <label>Tamaño :</label>
            <input
                  v-model.number="size"
                  class="tamaño--input"
                  type="number"
                  min="1"
                />
          </div>

          
        </div>

       
        
      </div>


       <div class="boton">
          <button @click="getCat">Quiero mi GifCat</button>
        </div>

        <div class="imagenGato ">
          <img :src="imgSrc" alt="Se supone que aca va un Gif Gatito" />
        </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      colorDefecto: "seleccione un color",
      colores: ["red", "blue", "yellow", "white", "green"],
      colorSelected: "",
      colorTraducidos: {
        red: "rojo",
        white: "blanco",
        green: "verde",
        yellow: "amarillo",
        blue: "azul",
      },
      filtroSelected: "",
      filtros: ["sepia", "blur", "mono", "negative", "paint", "pixel"],
      imgSrc: "",
      size: "",
      title: "",
    };
  },

  methods: {
    getCat() {
      this.imgSrc = `https://cataas.com/cat/gif/says/${this.title}?filter=${this.filtroSelected}&color=${this.colorSelected}&size=${this.size}`;
    },

    cambiarColor(color) {
      this.colorSelected = color;
    },

    cambiarFiltro(filtro) {
      this.filtroSelected = filtro;
    },
  },
};
</script>

<style>
h1,
h2 {
  text-align: center;
}
.imagen {
  width: 20px;
  height: 20px;
  border: solid 2px;
  border-radius: 50%;
  background-color: black;
 margin-left: 10px;
display: inline-block;
}

.titulo {
  text-align: center;

  height: 100px;
}

#main {
  background: red;
  height: 300px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.imagenGato {
  text-align: center;
  padding-bottom: 10px;
  background: cornflowerblue;
  padding-top: 10px;
  border-radius: 0 0 25px 25px;
 width: 600px;
}

.boton {
  text-align: center;
  padding: 10px;
  
}
.seccion {
  width: 600px;
  margin: auto;
  background: #ff5733;
  border: 1px aquamarine solid;
  border-radius: 25px;
}

body {
  background: green;
}


.seccion{
    width: 600px;
    margin: auto;
    background: #ff5733;
    border: 1px aquamarine solid;
    border-radius: 25px;
}

label{

 width: 100px;
display: inline-block;
}


select{

  width: 242px;
}
</style>
