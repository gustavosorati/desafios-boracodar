<template>
  <div class="player-control-container">
    <div class="controls">
      {{ index }}
      <button class="back" @click="back">
        <img src="../assets/play-back.svg" alt="voltar">
      </button>
  
      <button class="play" >
        <img src="../assets/play.svg" alt="voltar">
      </button>
  
      <button class="next" @click="next">
        <img src="../assets/play-back.svg" alt="voltar">
      </button>
    </div>

    <div class="progress" />

    <div class="footer">
      <span>03:20</span>

      <span>00:12</span>
    </div>
    
    <div>
      {{ current.title }}
    </div>


    <!-- <audio controls>
      <source v-bind:src="lists[index].src" type="audio/mp3"/>
    </audio> -->
    <!-- <div v-for="list in lists">
      <div>{{list.title}}</div>
    </div> -->
  </div>
</template>

<script>
  

  export default {
    name: "PlayerControls",
    props: {
      current: Object,
      index: Number,
      length: Number
    },
    // data() {
      // return {
    //     current: {},
    //     index: 0,
    //     lists: musics
    //   }
    // },
    // created() {
    //   this.current = this.lists[0]
    // },
    methods: {
      next() {
        const x = this.index + 1
        this.$emit('atualiza', x);
        // if(this.index < this.length - 1) {
        //   this.index++;
        //   // this.current = this.lists[this.index]
        // }
      },
      back() {
        if(this.index !== 0) {
          console.log('entrou sub')
          this.index--;
          // this.current = this.lists[this.index]
        }
      }
    }
  }
</script>

<style>
  .player-control-container {
    width: 100%;
    display: flex;
    flex-direction: column;
  }

  
</style>