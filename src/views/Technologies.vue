<template>
  <div id="app">
    <Header />

    <div class="nav">
      <p class="btn">
        <router-link class="btn" to="/acceuil">Home</router-link>
      </p>
      <p class="btn">
        <router-link class="btn" to="/sports">Sports</router-link>
      </p>
      <p class="btn">
        <router-link class="btn" to="/sante">Santé</router-link>
      </p>
      <p class="btn">
        <router-link class="btn" to="/divertissement"
          >Divertissement</router-link
        >
      </p>
      <p class="btn">
        <router-link class="btn" to="/sciences">Sciences</router-link>
      </p>
      <p class="btn">
        <router-link class="btn" to="/affaires">Affaires</router-link>
      </p>
    </div>
    <nav>
      <!--élément apparait que pour la partie smartphone-->
      <label for="toggle">☰</label>
      <input type="checkbox" id="toggle" />
      <div class="main_pages">
        <p class="btn">
          <router-link class="btn" to="/acceuil">Home</router-link>
        </p>
        <p class="btn">
          <router-link class="btn" to="/sports">Sports</router-link>
        </p>
        <p class="btn">
          <router-link class="btn" to="/sante">Santé</router-link>
        </p>
        <p class="btn">
          <router-link class="btn" to="/divertissement"
            >Divertissement</router-link
          >
        </p>
        <p class="btn">
          <router-link class="btn" to="/sciences">Sciences</router-link>
        </p>
        <p class="btn">
          <router-link class="btn" to="/affaires">Affaires</router-link>
        </p>
      </div>
    </nav>
    <h2>Technologies</h2>

    <div class="container1">
      <li v-for="item in posts" :key="item.id">
        <p>
          <a v-bind:href="item.url" rel="noopener" target="_blank"
            ><img class="photoarticle" :src="item.image" alt="..." /></a
          ><br />
        </p>
        <span
          ><span class="titre"
            ><a v-bind:href="item.url" rel="noopener" target="_blank">{{
              item.title
            }}</a>
            <br /><br
          /></span>
          <span class="description">{{ item.description }}</span
          ><br />
          <div class="source">
            <p>{{ item.source.name }}</p>
          </div>
          <div class="date">
            <p>{{ item.publishedAt.slice(2, 10) }}</p>
          </div>
        </span>
      </li>
    </div>
    <Footer />
  </div>
</template>

<script>
/* import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
}; */
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import axios from "axios";
export default {
  name: "Technologies",
  components: { Header, Footer },
  data() {
    return {
      posts: [],
    };
  },
  mounted() {
    // je récupère les données du profil connecté
    axios
      .get(
        "https://gnews.io/api/v4/top-headlines?token=8c90fa01a622015061484a9fcd8f1dc2&lang=fr&topic=technology"
      )

      .then((response) => {
        // console.log("réponse API", response);
        this.posts = response.data.articles;
      })
      .catch((error) => console.log(error));
  },
};
</script>

<style lang="scss">
$color-container: #ebebeb;
$colorsource-btnhover: #d52222;
$colortitre-date: #505050;

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  margin: 0px;
  padding: 0px;
}

.nav {
  display: flex;
  justify-content: space-around;
  background-color: $color-container;

  .btn {
    border: 2px;
    background-color: white;
    padding: 10px;
    border-radius: 10px 10px 10px 10px;
    text-decoration: none;
  }

  .btn:hover {
    color: white;
    background-color: $colorsource-btnhover;
  }
}

h2 {
  background-color: $color-container;
  margin: 0px;
  padding: 20px;
  text-transform: uppercase;
  letter-spacing: 2px;
  color: #000000;
}

.container1 {
  background-color: $color-container;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  width: 100%;

  li {
    width: 280px;
    height: 410px;
    margin: 20px;
    background-color: white;
    list-style: none;
    position: relative;
    overflow: hidden;
  }
  p {
    margin: 0px;
  }
  .photoarticle {
    width: 280px;
    height: 180px;
    margin: 0px;
    padding: 0px;
    display: block;
  }

  .titre a {
    font-size: 16px;
    color: $colortitre-date;
    text-decoration: none;
  }

  .titre a:hover {
    text-decoration: underline;
  }

  .description {
    color: #808080;
    font-size: 14px;
  }

  .source {
    position: absolute;
    bottom: 5px;
    left: 5px;
    color: $colorsource-btnhover;
    font-size: 14px;
    font-style: italic;
  }

  .date {
    position: absolute;
    bottom: 5px;
    right: 5px;
    font-size: 14px;
    color: $colortitre-date;
  }
}

nav, /*on enlève les éléments de la partie smartphone*/
label,
#toggle,
.main_pages {
  display: none;
}

@media only screen and (max-width: 768px) {
  .nav {
    /*on enlève la barre de nav de la partie pc*/
    display: none;
  }

  nav {
    /*DEBUT MENU BURGER*/
    display: block;
    /* height: 160px; */

    .main_pages {
      display: none;
      flex-direction: column;
      width: 60%;
      margin: auto;
      background-color: $color-container;

      border-radius: 10px 10px 10px 10px;
      // box-shadow: 3px 3px 5px 0px rgb(0 0 0 / 16%);
      padding-top: 0px;
      text-align: center;
      height: 300px;
      margin-bottom: 10px;
      margin-top: 10px;
      font-family: Verdana, Geneva, Tahoma, sans-serif;
    }

    .main_pages a {
      width: 50%;
      margin: auto;
      color: $colorsource-btnhover;
      text-decoration: none;
    }

    .main_pages a:hover {
      text-decoration: underline;
    }
  }

  label {
    width: 30px;
    display: flex;
    justify-content: center;
    position: absolute;
    top: 0px;
    right: 15px;
    align-items: center;
    margin: 0 auto;
    font-size: 50px;
    color: $colorsource-btnhover;
    cursor: pointer;
  }

  #toggle:checked + .main_pages {
    /*FIN MENU BURGER*/
    display: flex;
  }
}
</style>
