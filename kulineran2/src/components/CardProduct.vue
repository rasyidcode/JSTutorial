<template>
  <div class="card">
      <img :src="require('@/assets/images/' + product.gambar)" class="card-img-top" alt="product.nama">
      <div class="card-body">
        <h5 class="card-title">{{ product.nama }}</h5>
        <p class="card-text">
          Harga : Rp. {{ product.harga }}
        </p>
        <a href="#" class="btn btn-success"><b-icon-cart></b-icon-cart> Pesan</a>
      </div>
  </div>
</template>

<script>
export default {
    name: 'CardProduct',
    props: ['product']
}
</script>

<style>

</style>