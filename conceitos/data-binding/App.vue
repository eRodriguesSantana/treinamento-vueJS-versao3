<template>
  <div>
    <h1 v-bind:style="{ textDecoration: decoration }">Hello {{ name }}</h1>
    <input type="text" v-model="name">
    <br>
    <a v-bind:href="link">Link Para o Curso</a>
  </div>
</template>

<script>
export default {
    data: () => ({
        name: 'Eduardo',
        link: 'https://treinamento.vuejsbrasil.org',
        decoration: 'underline'
    })
}
</script>