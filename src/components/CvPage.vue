<script setup>
import { reactive, onMounted } from "vue";

var enEls = [];
var nlEls = [];
var jpEls = [];

const language = reactive({
  currentLanguage: "en",
});

onMounted(() => {
  enEls = document.querySelectorAll("html [lang='en']");
  nlEls = document.querySelectorAll("[lang='nl']");
  jpEls = document.querySelectorAll("[lang='jp']");

  nlEls.forEach((el) => {
    el.classList.toggle("language-disabled", true);
  });
  jpEls.forEach((el) => {
    el.classList.toggle("language-disabled", true);
  });
});

function changeLanguage(lang) {
  switch (language.currentLanguage) {
    case "en":
      enEls.forEach((el) => {
        el.classList.toggle("language-disabled", true);
      });
      break;

    case "nl":
      nlEls.forEach((el) => {
        el.classList.toggle("language-disabled", true);
      });
      break;

    case "jp":
      jpEls.forEach((el) => {
        el.classList.toggle("language-disabled", true);
      });
      break;

    default:
      break;
  }

  language.currentLanguage = lang;
  switch (lang) {
    case "en":
      enEls.forEach((el) => {
        el.classList.toggle("language-disabled", false);
      });
      break;

    case "nl":
      nlEls.forEach((el) => {
        el.classList.toggle("language-disabled", false);
      });
      break;

    case "jp":
      jpEls.forEach((el) => {
        el.classList.toggle("language-disabled", false);
      });
      break;

    default:
      break;
  }
}
</script>

<template>
  <div class="nav">
    <div class="left">
      <h1>CV</h1>
    </div>
    <div class="right">
      <ul class="navigation">
        <li>Balls</li>
        <li>Chicken</li>
        <li>Everytime</li>
        <li>I</li>
        <li>Find</li>
      </ul>
      <div class="languages">
        <span class="fi fi-gb" v-if="language.currentLanguage === 'en'"></span>
        <span
          class="fi fi-nl"
          v-else-if="language.currentLanguage === 'nl'"
        ></span>
        <span class="fi fi-jp" v-else></span>
        <div class="select-language">
          <span class="fi fi-gb" @click="changeLanguage('en')"></span>
          <span class="fi fi-nl" @click="changeLanguage('nl')"></span>
          <span class="fi fi-jp" @click="changeLanguage('jp')"></span>
        </div>
      </div>
    </div>
  </div>
  <div class="container">
    <div class="profile">
      <div class="photo">
        <img src="@/assets/images/cv.png" alt="" />
        <div class="info">
          <h1>Daniël Phoeng</h1>
          <p lang="en">Balls enjoyer</p>
          <p lang="nl">Ballen connoisseur</p>
          <p lang="jp">b ruh</p>
          <p lang="en">Balls enjoyer</p>
          <p lang="nl">Ballen connoisseur</p>
          <p lang="jp">b ruh</p>
        </div>
      </div>
      <div class="links"></div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
div.nav {
  display: flex;
  justify-content: space-between;
  box-shadow: 0 0 1rem 0 black;
  padding: 0rem 2rem;

  div.left {
    display: flex;
  }

  div.right {
    display: flex;
    align-items: center;
    column-gap: 2rem;

    ul {
      padding: 0;
      margin: 0;
    }

    ul.navigation {
      display: flex;
      list-style: none;
      li {
        padding: 1rem;
      }
    }
    div.languages {
      position: relative;
      span {
        font-size: 1.5rem;
      }
      > span {
        padding: 0.5rem 1rem;
      }

      &:hover {
        div.select-language {
          display: flex;
        }
      }
      div.select-language {
        display: none;
        position: absolute;
        flex-direction: column;
        row-gap: 0.5rem;
        border: 1px black solid;
        left: 50%;
        transform: translateX(-50%);
        padding: 0.5rem;
        background-color: rgba(0, 0, 0, 0.1);
        span {
          padding: 0rem 1rem;
          cursor: pointer;
        }
      }
    }
  }
}

.language-disabled {
  display: none;
}

div.container {
  display: flex;
  width: 100%;
  justify-content: center;
}

div.profile {
  display: flex;
  flex-direction: column;
  margin: 2rem;
  height: 50vh;
  width: 50%;

  // border: 1px solid black;
  div.photo {
    height: 90%;
    width: 100%;
    padding: 1rem;
    img {
      object-fit: cover;
      aspect-ratio: 1/1;
      height: 100%;
      border-radius: 50%;
      box-shadow: 0 0 1rem 0 black;
      float: left;
      margin-right: 3rem;
      shape-outside: circle();
      -webkit-shape-outside: circle();
    }
    div.info {
    }
  }
  div.links {
    display: flex;
    flex-direction: row;
    padding: 1rem;
    height: 10%;
  }
}
</style>
