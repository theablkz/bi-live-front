<template>
  <div class="container">
    <header-component />
    <catalog />
    <footer-component />
  </div>
</template>

<script>
import HeaderComponent from '~/components/layouts/header-component'
import FooterComponent from '~/components/layouts/footer-component'
import Catalog from '~/components/catalog'

export default {
  components: {
    HeaderComponent,
    FooterComponent,
    Catalog
  }
}
</script>

<style>

</style>
