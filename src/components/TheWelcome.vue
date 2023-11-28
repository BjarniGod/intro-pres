<template>
  <div id="flashcard-app" class="container">
    <h1>Bjarni Guðmann Jónsson</h1>
    <ul class="flashcard-list">
      <li v-for="(card, index) in cards" :key="index" v-on:click="toggleCard(card)">
        <transition name="flip">
          <div v-if="card.flipped" class="card back full-screen" :class="{ 'is-expanded': card.isExpanded }">{{ card.back }}</div>
          <div v-else class="card front" :style="{ backgroundImage: 'url(' + card.imageUrl + ')' }"></div>
        </transition>
      </li>
    </ul>
  </div>
</template>




<script>
import { VueFlip } from 'vue-flip';

export default {
  components: {
    'vue-flip': VueFlip
  },
  data() {
    return {
      cards: cards,
      newFront: '',
      newBack: '',
      error: false
    };
  },
  methods: {
    toggleCard(card) {
    card.flipped = !card.flipped;
    this.$nextTick(() => {
      card.isExpanded = card.flipped; // Expand the card if it is flipped
    });
  },
    addNew() {
      if (!this.newFront || !this.newBack) {
        this.error = true;
      } else {
        this.cards.push({
          front: this.newFront,
          back: this.newBack,
          flipped: false
        });
        this.newFront = '';
        this.newBack = '';
        this.error = false;
      }
    },
  }
};

const cards = [
    {
      front: 'Portrait',
      back: '',
      flipped: false,
      imageUrl: 'src/assets/img/portrait.jpg',
    },
    {
      front: 'Family',
      back: 'Information about my family!',
      flipped: false,
      imageUrl: 'assets/img/',
  
    },
    {
      front: 'Iceland',
      back: 'Information about Iceland!',
      flipped: false,
      imageUrl: 'assets/img/',
    },
    {
      front: 'Basketball',
      back: 'Information about basketball!',
      flipped: false,
      imageUrl: 'assets/img/',
    },
    {
      front: 'Home',
      back: 'Information about home!',
      flipped: false,
      imageUrl: 'assets/img/',
    },
    {
      front: 'Travels',
      back: 'Information about my travels!',
      flipped: false,
      imageUrl: 'assets/img/',
    },
    {
      front: 'Hobbies',
      back: 'Information about my hobbies!',
      flipped: false,
      imageUrl: 'assets/img/',
    },
    {
      front: 'Basketball',
      back: 'Information about basketball!',
      flipped: false,
      imageUrl: 'assets/img/',
    },
    {
      front: 'Basketball',
      back: 'Information about basketball!',
      flipped: false,
      imageUrl: 'assets/img/',
    },
    {
      front: 'Basketball',
      back: 'Information about basketball!',
      flipped: false,
      imageUrl: 'assets/img/',
    },
]; 
</script>
ç