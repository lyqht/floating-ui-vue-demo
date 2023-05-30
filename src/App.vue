<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import {ref} from 'vue';

import {
  useFloating,
  offset,
  flip,
  shift,
} from '@floating-ui/vue';
 
const reference = ref(null);
const floating = ref(null);
const isFloating = ref(false)
const { floatingStyles } = useFloating(reference, floating, {
  placement: 'top',
  middleware: [offset(10), flip(), shift()],
});

const toggleIsFloating = () => {
  isFloating.value = !isFloating.value;
}
</script>

<template>
  <header>
    <img ref="reference" alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" @click="toggleIsFloating" />

      <HelloWorld v-if="isFloating" ref="floating" :style="floatingStyles" msg="You did it!" />
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
