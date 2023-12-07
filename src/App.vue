<template>
  <flashcard-list @card-selected="selectedCard = $event"></flashcard-list>
  <expanded-card v-if="selectedCard" :card="selectedCard"></expanded-card>
</template>

<script>
import FlashcardList from './components/FlashcardList.vue';
import ExpandedCard from './components/ExpandedCard.vue';

export default {
  components: {
    FlashcardList,
    ExpandedCard
  },
  data() {
    return {
      selectedCard: null
    };
  }
};
</script>
