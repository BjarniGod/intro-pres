<template>
  <div id="flashcard-app" class="container">
    <h1>Bjarni Guðmann Jónsson</h1>
    <ul class="flashcard-list">
    <li v-for="(card, index) in cards" :key="index" @click="toggleCard(card, index)">
        <div v-if="card.flipped" class="card back">{{ card.back }}</div>
        <div v-else class="card front">{{ card.front }}</div>
      </li>
    </ul>
    <expanded-card v-if="selectedCard" :card="selectedCard" :index="selectedIndex" @close="selectedCard = null"></expanded-card>
  </div>
</template>

<script>
import ExpandedCard from './ExpandedCard.vue';

export default {
  components: {
    ExpandedCard
  },
  data() {
    return {
      cards: cards,
      selectedCard: null,
      selectedIndex: null
    };
  },
methods: {
  toggleCard(card, index) {
    this.selectedCard = card;
    this.selectedIndex = index;
  }
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