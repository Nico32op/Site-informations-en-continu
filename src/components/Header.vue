<template>
  <div id="app">
    <div class="header">
      <h1>
        <router-link class="btn" to="/acceuil">Info en continu</router-link>
      </h1>
      <p class="news">News provenant de l'API GNEWS</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  height: 80px;
}

.header h1 {
  margin: 0px;
  padding: 0px;
  margin-top: 20px;
  margin-left: 20px;
  text-transform: uppercase;
  font-size: 28px;
  letter-spacing: 2px;
  color: #000000;
  text-decoration: none;
}

.header h1 a {
  text-decoration: none;
  color: #000000;
}

.header .news {
  padding-top: 30px;
  margin: 0px;
  margin-right: 20px;
  text-transform: uppercase;
  color: #000000;
}

@media only screen and (max-width: 768px) {
  .header {
    flex-direction: column;
  }

  .header h1 {
    font-size: 22px;
    margin-top: 7px;
  }
  .header .news {
    text-align: center;
    font-size: 14px;
  }
}

@media (max-width: 350px) {
  .header h1 {
    font-size: 17px;
  }
}
</style>
