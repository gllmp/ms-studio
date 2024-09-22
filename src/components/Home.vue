<template>
  <div class="home-container">
    <div class="home-header">
      <a href="./">
        <img src="../assets/img/msstrs-logo.png" class="logo" alt="manami seki space time research studio logo" />
      </a>
      <!-- <Logo /> -->
    </div>
    <div class="home-content">
      <div>
        <p>Hello.</p>
        <p>This is Manami Seki Space Time Research Studio.</p>
      </div>
      <div>
        <p>Manami Seki is a media artist based in Paris and Tokyo.</p>
        <p>Her works focus on the exchange process between language, image, the physical and the multidimensional space.</p>
      </div>
      <div>
        <p><a class="underline" href="/pdf/Manami-Seki-CV.pdf" target="_blank">CV</a> / <a class="underline" href="/pdf/Manami-Seki-Portfolio.pdf" target="_blank">Portfolio</a></p>
      </div>
      <div>
        <p class="home-contact">contact: <a ref="contactLink" href="mailto:manamiro2@gmail.com">manamiro2[at]gmail[dot]com</a></p>
      </div>
      <div class="home-credit">
        <p class="credit-font">Typeface: <a href="https://velvetyne.fr/fonts/terminal-grotesque/" target="_blank">Terminal Grotesque</a> by <a href="https://raphaelbastide.com/" target="_blank">Raphaël Bastide</a> & Jérémy Landes.</p>
        <p class="credit-web">Website by <a href="https://www.instagram.com/_.gcode/" target="_blank">Guillaume Piccarreta</a></p>
      </div>
      <Type />
    </div>
  </div>
  <div class="copyright">
    <p>Copyright © {{ year }} Manami Seki</p>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
// import Logo from './Logo.vue'
import Type from './Type.vue'

defineProps<{ msg?: string }>()

const contactLink = ref<HTMLLinkElement>()

const year = ref(new Date().getFullYear())
</script>

<style lang="scss" scoped>
.logo {
  height: 5rem;
}
.home-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100%;
}
.home-header {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: flex-start;
  width: 100%;
  height: 30%;
  padding-right: 1rem;
}
.home-content {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  text-align: center;
  padding: 1rem;
  padding-top: 0;
  padding-left: 1.6rem;
  font-size: 32px;

  div {
    margin-bottom: 3rem;
  }

  p {
    font-size: 1.5rem;
    text-align: left;
  }

  .home-contact {
    font-size: 1.2rem;
  }

  .home-credit {
    margin-bottom: 0;

    p, a {
      font-size: 1rem;
      color: #aeaeae;
    }
  }
}

.copyright {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  margin-bottom: 0.2rem;

  p {
    font-size: 0.8rem;
  }
}
</style>
