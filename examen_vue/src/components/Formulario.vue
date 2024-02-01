<template>
  <div>
    <b-form
      @submit="onSubmit"
      @reset="onReset"
      v-if="show"
      action="https://vuejs.org/"
      method="post"
    >
      <b-form-group id="form-group-brand" label="Marca" label-for="brand">
        <b-form-input
          id="brand"
          v-model="form.brand"
          type="text"
          placeholder="Ingrese la marca del auto"
          required
        >
        </b-form-input>
      </b-form-group>

      <b-form-group id="form-group-model" label="Modelo" label-for="model">
        <b-form-input
          id="model"
          v-model="form.model"
          type="text"
          placeholder="Ingrese el modelo del auto"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="form-group-serie" label="Serie" label-for="serie">
        <b-form-input
          id="serie"
          v-model="form.serie"
          type="text"
          placeholder="Ingrese el numero de serie del auto"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="form-group-year" label="Año" label-for="year">
        <b-form-input
          id="year"
          v-model="form.year"
          type="text"
          placeholder="Ingrese el año del auto"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Enviar</b-button>
      <b-button type="reset" variant="danger">Limpiar</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from "axios";
import Vue from "vue";
export default Vue.extend({
  data() {
    return {
      form: {
        brand: "",
        model: "",
        serie: "",
        year: "",
      },
      show: true,
    };
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();
      const brand = form.brand;
      const model = form.model;
      const serie = form.serie;
      const year = form.year;

      axios.post("http://localhost:8080/api/vehiculos", {
        brand,
        model,
        serie,
        year,
      });
    },
    onReset(event) {
      event.preventDefault();
      (this.form.brand = ""),
        (this.form.model = ""),
        (this.form.serie = ""),
        (this.form.year = ""),
        (this.show = false),
        this.$nextTick(() => {
          this.show = true;
        });
    },
  },
});
</script>

<style>
</style>