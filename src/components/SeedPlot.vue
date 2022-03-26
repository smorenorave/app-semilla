<template>
  <div class="hello">
    <h2>Bienvenido al simulador de siembra</h2>
    <div>
      <form @submit="sendData" >
        <h5>¿Qué materia prima desea cosechar?</h5>

        <div class="fr-form">
          <b-form-select
            id="formSeed"
            v-model="selectedSeed"
            :options="optionsSeed"
          ></b-form-select>
        </div>

        <h5>¿En cuál parcerla desea sembrar?</h5>

        <div class="fr-form">
          <b-form-select
            id="formPlot"
            v-model="selectedPlot"
            :options="optionsPlot"
          ></b-form-select>
        </div>

        <p>
          <b-card>
            <input
              class="btn btn-outline-success fr-botton"
              type="submit"
              value="Enviar"
            />

            <input
              class="btn btn-outline-danger fr-botton"
              type="reset"
              value="Borrar"
            />
          </b-card>
        </p>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      data:{seed:null,plot:null},
      selectedSeed: null,
      optionsSeed: [
        { value: null, text: "Seleccione una semilla" },
        { value: "corn", text: "Maíz" },
        { value: "potato", text: "Papa" },
        { value: "carrot", text: "Zanahora" },
        { value: "coffee", text: "Café" }
      ],

      selectedPlot: null,
      optionsPlot: [
        { value: null, text: "Seleccione una parcela" },
        { value: 107019, text: "Frontino" },
        { value: 106977, text: "Girardota" },
        { value: 106956, text: "La ceja" },
      ],
    };
  },

  methods: {
    sendData: async function () {
      
      alert(
        JSON.stringify(
          " se ha selecionado la semilla " +
            this.selectedSeed + 
            " para la parcela " +
            this.selectedPlot
        )
      );
      this.data = {
        seed: this.selectedSeed,
        plot: this.selectedPlot
      };
      await axios.post("http://localhost:8080/project/create",this.data);

      
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.fr-botton {
  margin-left: 10px;
  margin-right: 10px;
}

.fr-form {
  margin-left: 3px;
  margin-right: 3px;
}
</style>
