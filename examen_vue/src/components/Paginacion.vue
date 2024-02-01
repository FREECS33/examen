<template>
  <b-container class="mt-5">
    <b-button href="/home" variant="primary">Regresar</b-button>
    <b-input placeholder="buscar" v-model="filtro"></b-input>
    <b-table
      id="my-table"
      :items="autos"
      :per-page="perPage"
      :current-page="currentPage"
      :fields="fields"
      :sort-by.sync="sortBy"
      :sort-desc.sync="sortDesc"
      label-sort-asc=""
      label-sort-desc=""
      small
      :filter="filtro"
      @filtered="onFiltered"
    >
    </b-table>
    <div class="overflow-auto">
      <b-pagination
        v-model="currentPage"
        :total-rows="rows"
        :per-page="perPage"
        aria-controls="my-table"
      ></b-pagination>

      <p class="mt-3">Current Page: {{ currentPage }}</p>
    </div>
  </b-container>
</template>
  
  <script>
import auto from '../car/auto';

export default {
  data() {
    return {
      filtro: null,
      sortBy: "name",
      sortDesc: false,
      perPage: 5,
      rows: 0,
      currentPage: 1,
      autos: [],
      fields: [
        { key: "brand", label: "Marca", sortable: true },
        { key: "model", label: "Modelo", sortable: true },
        { key: "serie", label: "Serie", sortable: true },
        { key: "year", label: "Año", sortable: true },
      ],
    };
  },
  mounted() {
  },
  methods: {
    async obtenerautos() {
      try {
        const data = await auto.obtenerAutosPaginados(
          parseInt(this.currentPage),
          parseInt(this.perPage),
          this.sortBy
        );
        this.autos = data.content;
        this.rows = this.autos.length;
      } catch (error) {
        console.error(error);
      }
    },
    onFiltered(filteredItems) {
      this.currentPage = 1;
      this.rows = filteredItems.length;
    },
  },
};
