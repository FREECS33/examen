<template>
  <div>
    <b-card
      title="Pagina de inicio"
      img-src="https://picsum.photos/600/300/?image=25"
      img-alt="Image"
      img-top
      tag="article"
      style="max-width: 20rem"
      class="mb-2"
    >
      <b-card-text>
        Estas en la pagina de inico, usa lo botones de la perte inferior para
        navegar
      </b-card-text>

      <b-button href="/formulario" variant="primary">Formulario</b-button>
      <b-button href="/paginacion" variant="primary"
        >Lista de registros</b-button
      >
    </b-card>
  </div>
</template>

<script>
export default {};
</script>

<style>
</style>