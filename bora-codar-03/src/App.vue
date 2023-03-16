<script setup>
  import Button from './components/Button.vue'
</script>

<template>
  <table id="projeto" cellpadding="0" cellspacing="0">
    <thead>
      <tr>
        <th></th>
        <th>BOTÃO PRIMÁRIO</th>
        <th>BOTÃO SECUNDÁRIO</th>
        <th>BOTÃO TERCIÁRIO</th>
        <th>CURSOR</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td class="type">DEFAULT</td>
        <td><Button text="DEFAULT primary" /></td>
        <td><Button text="default secondary" variant="secundary" /></td>
        <td><Button text="DEFAULT tertiary" variant="tertiary" /></td>
      </tr>
      <tr>
        <td class="type">HOVER</td>
        <td><Button text="HOVER primary" /></td>
        <td><Button text="HOVER secondary" variant="secundary" /></td>
        <td><Button text="HOVER tertiary" variant="tertiary" /></td>
      </tr>
      <tr>
        <td class="type">FOCUS</td>
        <td><Button text="FOCUS primary" isFocused /></td>
        <td><Button text="FOCUS secondary" variant="secundary" isFocused /></td>
        <td><Button text="FOCUS tertiary" variant="tertiary" isFocused /></td>
      </tr>
      <tr>
        <td class="type">DISABLED</td>
        <td><Button text="DISABLED primary" disabled /></td>
        <td><Button text="DISABLED secondary" variant="secundary" disabled /></td>
        <td><Button text="DISABLED tertiary" variant="tertiary" disabled /></td>
      </tr>
      <tr>
        <td class="type">LOADING</td>
        <td><Button text="LOADING primary" isLoading /></td>
        <td><Button text="LOADING secondary" variant="secundary" isLoading /></td>
        <td><Button text="LOADING tertiary" variant="tertiary" isLoading /></td>
      </tr>
      <tr>
        <td class="type">MOVABLE</td>
        <td><Button text="MOVABLE primary" isMovable /></td>
        <td><Button text="MOVABLE secondary" variant="secundary" isMovable /></td>
        <td><Button text="MOVABLE tertiary" variant="tertiary" isMovable /></td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
  #projeto {
    border: none;
  }

  #projeto thead, .type {
    background-color: #1C162C;
  }

  #projeto .type {
    padding: 1rem 2rem;
  }

  #projeto thead th {
    padding: 1rem 2rem;
  }

  #projeto tbody td {
    text-align: center;
    padding: 1rem 1rem;
  } 
</style>
