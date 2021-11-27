<template>
  <footer>
    <p class="textefooter">Réalisé par Leonardi Nicolas</p>
    <p>
      <a
        href="https://nico32op.github.io/Nicolas-Leonardi/"
        rel="noopener"
        target="_blank"
        >Mes autres créations sont disponibles sur mon Portfolio</a
      >
    </p>
  </footer>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style lang="scss">
footer {
  text-align: center;
  .textefooter {
    font-weight: 600;
  }
  a {
    // text-decoration: none;
    color: #d52222;
    font-style: italic;
  }
  a:hover {
    color: #2d3436;
    text-decoration: underline;
  }
}
</style>
