<template>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
// @ts-ignore
import Two from 'https://cdn.skypack.dev/two.js@latest'

const isMobile = ref(false);
// const isMobile = window.navigator.maxTouchPoints > 0;
// const message = isMobile ? 'Tap Me' : 'Start Typing';

onMounted(() => {
  isMobile.value = /Mobi|Android/i.test(navigator.userAgent);
});

// Initialize an instance to render
// render to the screen. Try changing
// the `type` property to:
//   Two.Types.canvas
//   Two.Types.webgl
// To see different rendering styles.
const two = new Two({
  type: Two.Types.svg,
  fullscreen: true,
  autostart: true
}).appendTo(document.body);

// Change the background
two.renderer.domElement.style.background = '#ddd';

// Create an array to keep track of the 
// the different characters which will be added.
const characters: string[] = [];

// Set the gravity of the world.
// Try changing the x and y components
// to change the "falling" animation
const gravity = new Two.Vector(0, 0.66);

// The font styles to apply to
// all text in the scene.
let styles = {
  family: 'TerminalGrotesque, sans-serif',
  size: 100,
  leading: 50,
  weight: 900
};

// Create text that informs the user
// on what they should do to interact
// with this example.
// const directions = two.makeText(message, two.width / 2, two.height / 2, styles);
// directions.fill = 'white';

// Add events to the page
window.addEventListener('mousedown', keydown, false);
window.addEventListener('keydown', keydown, false);
window.addEventListener('touchstart', touchstart, false);

// Add callbacks to events that Two.js triggers.
two.bind('resize', resize);
two.bind('update', update);

// Handle keydown event and add
// the pressed letter to the scene.
function keydown() {
  // const character = String.fromCharCode(e.which);
  const characters = ['M', 'S', 'T', 'R'];
  const character = characters[Math.floor(Math.random()*characters.length)]
  add(character);
}

// Handle touchstart event
function touchstart() {
  // const character = String.fromCharCode(e.which);
  const characters = ['M', 'S', 'T', 'R'];
  const character = characters[Math.floor(Math.random()*characters.length)]
  add(character);
}

// Set the position of the directions
// to the center of the page.
function resize() {
  //directions.translation.set(two.width / 2, two.height / 2);
}

// An update callback that is called every time
// the scene is rendered. Think of this as an
// animation loop.
function update() {

  // Iterate through all letters in the `characters`
  // array, apply gravity to their velocity, and
  // update their respective position.
  for (let i = 0; i < characters.length; i++) {

    const text = characters[i];
    // @ts-ignore
    text.translation.addSelf(text.velocity);
    // @ts-ignore
    text.rotation += text.velocity.r;
    // @ts-ignore
    text.velocity.add(gravity);

    // If the text's velocity is greater than 0
    // and the position is off the page, then
    // remove the text.
    // @ts-ignore
    if (text.velocity.y > 0 && text.translation.y > two.height) {
      two.scene.remove(text);
      two.release(text);
      characters.splice(i, 1);
    }
  }
}

// Utility function to add a `Two.Text`
// instance to the scene, set its styles
// and create a velocity and rotation
// to be applied in the update callback.
function add(msg: any) {

  const x = (Math.random() * two.width) / 2 + two.width / 4;
  const y = two.height * 1.25;

  const r = Math.floor(Math.random() * (150 - 50) + 50);
  styles.size = r;

  const text = two.makeText(msg, x, y, styles);
  text.size *= 3;
  text.fill = '#333';

  text.velocity = new Two.Vector();
  text.velocity.x = 10 * (Math.random() - 0.5);
  text.velocity.y = -(20 * Math.random() + 15);
  text.velocity.r = (Math.random() * Math.PI) / 100;

  characters.push(text);
}
</script>