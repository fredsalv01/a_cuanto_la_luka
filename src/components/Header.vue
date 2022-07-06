<template>
  <header class="header">
    <nav class="header__nav">
      <a href="/a_cuanto_la_luka/" class="header__logo">
        <span class="header__logo--img"></span>
        <span class="header__logo--name">
          A <span>cuánto</span> la <span>luka</span>
        </span>
      </a>
      <ion-icon @click="toggleMenu" name="menu-outline" class="header__toggle" id="toggle-menu"></ion-icon>
      
      <ul class="nav-menu">
        <li class="nav-menu__item">
          <a href="#hero" class="nav-menu__link">Inicio</a>
        </li>
        <li class="nav-menu__item">
          <a href="#about" class="nav-menu__link">Acerca</a>
        </li>
        <li class="nav-menu__item">
          <a href="#contact" class="nav-menu__link">Contacto</a>
        </li>
        <li class="nav-menu__item">
          <a href="#newsletter" class="nav-menu__link">Noticias</a>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    let links = [
      {
        name: "Inicio",
        href: "#hero",
      },
      {
        name: "Acerca de",
        href: "#about",
      },
      {
        name: "Contacto",
        href: "#contact",
      },
      {
        name: "Noticias",
        href: "#newsletter",
      },
    ],
    toggleMenu = () => {
      let menu = document.querySelector(".nav-menu");
      menu.classList.toggle("active");
    }

    return {
      links,
      toggleMenu,
    };
  },
};
</script>
