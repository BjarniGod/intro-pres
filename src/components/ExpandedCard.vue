<template>
  <div class="expanded-card-overlay" @click="close">
    <div class="expanded-card-content" :class="cardColorClass">
      {{ card.back }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    card: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  },
  computed: {
    cardColorClass() {
        if (this.index < 3) return 'color-1';
        if (this.index % 2 === 0) return 'color-2';
        if (this.index % 4 === 3) return 'color-3';
        if ((this.index + 2) % 5 === 0) return 'color-4';
        if ((this.index + 4) % 4 === 0) return 'color-5';
        if ((this.index + 7) % 7 === 0) return 'color-6';
        return 'default-color';
    }
  },
  methods: {
    close() {
      this.$emit('close');
    }
  }
};
</script>