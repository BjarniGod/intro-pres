<template>
  <div id="flashcard-app" class="container">

<h1>Bjarni Guðmann Jónsson</h1>

<ul class="flashcard-list">
  <li v-on:click="toggleCard(card)" v-for="(card, index) in cards">
    <transition name="flip">
      <p v-bind:key="card.flipped" class="card">
          {{ card.flipped ? card.back : card.front }}
      </p>
    </transition>
  </li>
</ul>
</div>
</template>

<script>
const cards = [
    {
      front: 'Portrait',
      back: 'Information about me!',
      flipped: false,
    },
    {
      front: 'Family',
      back: 'Information about my family!',
      flipped: false,
  
    },
    {
      front: 'Iceland',
      back: 'Information about Iceland!',
      flipped: false,
    },
    {
      front: 'Basketball',
      back: 'Information about basketball!',
      flipped: false,
    },
    {
      front: 'Home',
      back: 'Information about home!',
      flipped: false,
    },
    {
      front: 'Travels',
      back: 'Information about my travels!',
      flipped: false,
    },
    {
      front: 'Hobbies',
      back: 'Information about my hobbies!',
      flipped: false,
    },
    {
      front: 'Basketball',
      back: 'Information about basketball!',
      flipped: false,
    },
    {
      front: 'Basketball',
      back: 'Information about basketball!',
      flipped: false,
    },
    {
      front: 'Basketball',
      back: 'Information about basketball!',
      flipped: false,
    },
]; 

export default {
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
    deleteCard(index) {
      this.cards.splice(index, 1);
    }
  }
};
</script>

<style>
body {
  font-family: 'Montserrat', sans-serif;
  text-align: center;
  background: black;
}

h1 {
  color: white;
}

ul {
  padding-left: 0;
  display: flex;
  flex-flow: row wrap;
}

li {
  list-style-type: none;
  padding: 10px 10px;
  transition: all 0.3s ease;
}

.container {
  max-width: 100%;
  padding: 2em;
}

.wrapper {
  
}

.card {
  display: block;
  width: 150px;
  height: 175px;
  padding: 80px 50px;
  background-color: #51aae5;
  border-radius: 7px;
  margin: 5px;
  text-align: center;
  line-height: 27px;
  cursor: pointer;
  position: relative;
  color: #fff;
  font-weight: 600;
  font-size: 20px;
  -webkit-box-shadow: 9px 10px 22px -8px rgba(209,193,209,.5);
  -moz-box-shadow: 9px 10px 22px -8px rgba(209,193,209,.5);
  box-shadow: 9px 10px 22px -8px rgba(255, 255, 255, 0.5);
  will-change: transform;
}

li:hover{
  transform: scale(1.1);
}

li:nth-child(-n+3) .card{
  background-color: #e65f51;
  }

li:nth-child(2n+1) .card{
  background-color: #a17de9;
  }

li:nth-child(4n) .card{
  background-color: #feca34;
  }

li:nth-child(5n-2) .card{
  background-color: #51aae5;
  }

li:nth-child(4n+4) .card{
  background-color: #feca34;
  }

li:nth-child(-7n+7) .card{
  background-color: #e46055;
  }

.delete-card {
  position: absolute;
  right: 0;
  top: 0;
  padding: 10px 15px;
  opacity: .4;
  transition: all 0.5s ease;
}

.delete-card:hover, .error {
  opacity: 1;
  transform: rotate(360deg);
}

.flip-enter-active {
  transition: all 0.4s ease;
}

.flip-leave-active {
  display: none;
}

.flip-enter, .flip-leave {
  transform: rotateY(180deg);
  opacity: 0;

}

/* Form */
.flashcard-form{
  position: relative;
}


label{
  font-weight: 400;
  color: #333;
  margin-right: 10px;
}

input{
  border-radius: 5px;
  border: 2px solid #eaeaea;
  padding: 10px;
  outline: none;
}

button{
  border-radius: 5px;
  border: 1px solid #87cb84;
  background-color: #87cb84;
  padding: 8px 15px;
  outline: none;
  font-size: 14px;
  font-weight: 700;
  color: #fff;
  cursor: pointer;
  transition: all 0.3s ease;
}

button:hover{
  background-color: #70a66f;
}

.error{
  margin-top: 10px;
  display: block;
  color: #e44e42;
  font-weight: 600;
}

</style>