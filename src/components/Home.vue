<script setup lang="ts">
// import { ref } from 'vue'

defineProps<{ msg?: string }>()

// const clicks = ref(0)
</script>

<template>
  <div class="home-container">
    <div class="home-header">
      <a href="./">
        <img src="../assets/msstrs-logo.jpg" class="logo" alt="manami seki space time research studio logo" />
      </a>
      <!-- <h1>Manami Seki</h1> -->
    </div>
    <!-- <div class="card">
      <button type="button" @click="clicks++">you clicked {{ clicks }} time{{ clicks <= 1 ? '' : 's' }}</button>
    </div> -->
    <div class="home-content">
      <p>Hello.</p>
      <p>My name is <span class="underline">Manami Seki.</span></p>
      <p>I am an <span class="underline">artist</span> from <span class="underline">Tokyo</span>, Japan.</p>
      <p>You can find my portfolio <a class="underline" href="/portfolio.pdf" target="_blank">here</a></p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.logo {
  height: 5rem;
}
.home-container {
  display: flex;
  flex-direction: column;
}
.home-header {
  display: flex;
  flex-direction: row;
  align-items: flex-end;
}
.home-content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 1rem;
  padding-left: 1.6rem;

  p {
    font-size: 1.5rem;
    text-align: left;
  }
}
</style>
