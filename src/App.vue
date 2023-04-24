<template>
  <header>
  <div class="botoes">
    <router-link :to="{ name: 'home' }">Home</router-link> <br>
    <router-link to="/categorias">Categorias</router-link> <br>
    <router-link to="/editoras">Editoras</router-link> <br>
    <router-link to="/livros">Livros</router-link> <br>
  </div>
  </header>
  <main>
    <RouterView />
  </main>
</template>

<style>

.botoes {
  background-color: gray;
  border-radius: 20px;
  text-align: center;
};

</style>
