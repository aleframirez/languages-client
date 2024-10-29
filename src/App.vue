<template>
  <header>
    <div class="container">
      <RouterLink class="logo" to="/">
        <img src="./assets/temple.png" width="32" height="32" alt="Home Icon" />
      </RouterLink>
      <nav :class="{ active: isNavbarActive }" class="navbar">
        <ul class="navbar-list">
          <li>
            <RouterLink class="navbar-link" to="/about">About us</RouterLink>
          </li>
          <li>
            <RouterLink class="navbar-link" to="/">How we work</RouterLink>
          </li>
          <li>
            <RouterLink class="navbar-link" to="/">Contact</RouterLink>
          </li>
          <li>
            <RouterLink class="navbar-link" to="/">FAQ</RouterLink>
          </li>
          <li>
            <RouterLink class="navbar-link" to="/login">LogIn</RouterLink>
          </li>
        </ul>
      </nav>

      <button
        class="nav-open-btn"
        @click="toggleNavbar"
        :class="{ active: isNavToggleActive }"
      >
        <ion-icon
          name="menu-outline"
          aria-hidden="true"
          class="menu-icon"
        ></ion-icon>
        <ion-icon
          name="close-outline"
          aria-hidden="true"
          class="close-icon"
        ></ion-icon>
      </button>

      <div
        class="overlay"
        data-overlay
        :class="{ active: isOverlayActive }"
        @click="toggleNavbar"
      ></div>
    </div>
    <!-- <a href="https://www.flaticon.com/free-icons/japan" title="japan icons"
      >Japan icons created by Freepik - Flaticon</a
    > -->
  </header>

  <RouterView />
</template>

<script setup>
import { ref } from "vue";
import { RouterLink, RouterView } from "vue-router";

const isNavbarActive = ref(false);
const isNavToggleActive = ref(false);
const isOverlayActive = ref(false);

// Function to toggle navbar state
const toggleNavbar = () => {
  isNavbarActive.value = !isNavbarActive.value;
  isNavToggleActive.value = !isNavToggleActive.value;
  isOverlayActive.value = !isOverlayActive.value;
  // document.body.classList.toggle("nav-active");
};
</script>

<style scoped>
header {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  padding-block: 30px;
  z-index: 4;
}

header .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

header .logo img {
  width: 46px;
}

.nav-open-btn {
  color: var(--text-white);
  font-size: 3rem;
}

.nav-open-btn.active .menu-icon,
.nav-open-btn .close-icon {
  display: none;
}

.nav-open-btn .menu-icon,
.nav-open-btn.active .close-icon {
  display: block;
}

.navbar {
  position: absolute;
  top: 100%;
  right: 16px;
  background-color: var(--bg-vivid-kurenai);
  color: var(--text-white);
  padding: 16px 30px;
  border-radius: var(--radius-24);
  opacity: 0;
  visibility: hidden;
  transition: 500ms var(--cubic-out);
  z-index: 1;
}

.navbar.active {
  opacity: 1;
  visibility: visible;
  transform: translate(-15px);
}

.navbar-list > li:not(:last-child) {
  margin-block-end: 5px;
}

.navbar-link {
  font-weight: var(--weight-medium);
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  pointer-events: none;
}

.overlay.active {
  pointer-events: all;
}

/*-----------------------------------*\
  #MEDIA QUERIES
\*-----------------------------------*/

/*
  Responsive for larger than 575px screen
*/

@media (min-width: 575px) {
  /*
    REUSED STYLE
  */

  .container {
    max-width: 500px;
    width: 100%;
    margin-inline: auto;
  }

  /*
    HEADER
  */

  header .container {
    max-width: unset;
  }
}

/*
  Responsive for larger than 768px screen
*/

@media (min-width: 768px) {
  /*
    CUSTOM PROPERTY
  */

  :root {
    /*
      TYPOGRAPHY
    */

    /* font-size */
    --fontSize-1: 5.5rem;
    --fontSize-2: 4rem;

    /*
      SPACING
    */

    --section-spacing: 150px;
  }

  /*
    REUSED STYLE
  */

  .container {
    max-width: 720px;
  }

  /*
    HEADER
  */

  header .btn {
    display: grid;
    margin-inline: auto 30px;
  }
}

/*
  Responsive for larger than 992px screen
*/

@media (min-width: 992px) {
  /*
    REUSED STYLE
  */

  .container {
    max-width: 960px;
    padding-inline: 40px;
  }

  body.nav-active {
    overflow: auto;
  }

  /*
    HEADER
  */

  .nav-open-btn,
  .overlay {
    display: none;
  }

  header .logo img {
    width: 52px;
  }

  .navbar,
  .navbar.active {
    all: unset;
    margin-inline-start: 80px;
  }

  .navbar-list {
    display: flex;
    align-items: center;
    gap: 40px;
  }

  .navbar-list > li:not(:last-child) {
    margin-block-end: 0;
  }

  .navbar-link {
    color: var(--text-white);
    transition: var(--transition-1);
  }

  .navbar-link:is(:hover, :focus-visible) {
    color: var(--text-white-alpha-60);
  }

  header .btn {
    margin-inline-end: 0;
  }
}

/*
  Responsive for larger than 1200px screen
*/

@media (min-width: 1200px) {
  /*
    CUSTOM PROPERTY
  */

  :root {
    /*
      TYPOGRAPHY
    */

    --fontSize-1: 7rem;
    --fontSize-3: 2.8rem;
  }

  /*
    REUSED STYLE
  */

  .container {
    max-width: 1140px;
  }
}

/*
  Responsive for larger than 1400px screen
*/

@media (min-width: 1400px) {
  /*
    CUSTOM PROPERTY
  */

  :root {
    /*
      TYPOGRAPHY
    */

    /* font size */

    --fontSize-1: 8rem;
  }

  /*
    REUSED STYLE
  */

  .container {
    max-width: 1350px;
  }
}
</style>
