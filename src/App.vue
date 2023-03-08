<script setup lang="ts">
  import {ref, reactive, computed} from 'vue';

  let product = reactive({
    image: true
  })

  const icon = ref('/360svg.svg');

  function changeImageState() {
    product.image = !product.image,
    icon.value = icon.value === '/360svg.svg' ? '/close.svg' : '/360svg.svg';
  }

  const productImage = computed(() => {
    return product.image ? '/sofa.gif' : '/sofa.png'
  });
</script>

<template>
  <section id="products-page">
    <div class="left-side">
      <img 
        :src="productImage" alt="Sofá"
      >

      <img 
        class="rotate"
        :src="icon" alt="rotacionar em 360° graus"
        @click="changeImageState"
      >     
    </div>

    <div class="right-side">
      <span class="code">Código: 42404</span>
      <h1>Sofá Margot II - Rosé</h1>

      <span class="price">R$ 4.000,00</span>
      <button>Adicionar a cesta</button>
    </div>
  </section>
</template>

<style scoped>
  #products-page {
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #D9CDF7;
  }

  .left-side, .right-side {
    width: 600px;
    height: 600px;
    padding: 1rem;
  }

  .left-side {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .left-side img:first-child {
    width: 100%;
  }

  .left-side img:last-child {
    cursor: pointer;
  }

  .left-side .rotate {
    position: absolute;
    top: 120px;
    right: 60px;
  }

  .right-side {
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 1rem;
  }

  .right-side .code {
    font-size: 14px;
    font-weight: 300;
    color: #271A45;
    text-transform: uppercase;
    font-family: 'Lato', sans-serif;
  }

  .right-side h1 {
    font-weight: 600;
    font-size: 2rem;
    font-family: 'Crimson Pro', serif;
  }

  .right-side .price {
    font-size: 1rem;
    font-weight: 400;
    color: #271A45;
    text-transform: uppercase;
    font-family: 'Lato', sans-serif;
  }

  .right-side button {
    width: 150px;
    padding: 8px 16px;
    border-radius: 999px;
    background: transparent;
    border: .5px solid #271A45;

    font-size: .75rem;
    font-weight: 400;
    text-transform: uppercase;
    font-family: 'Lato', sans-serif;

    cursor: pointer;
  }
</style>
