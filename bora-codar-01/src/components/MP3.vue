<template>
  <div class="container">
    <!-- COVER -->
    <div class="cover">
      <img v-bind:src="current.cover" />
    </div>
    
    <!-- MUSIC -->
    <div class="music-info">
      <h1>{{current.title}}</h1>
      <h3>{{current.album}}</h3>
    </div>

    <div class="options">
      <!-- CONTROLS -->
      <div class="controls">
        <button class="back" @click="back">
          <img src="../assets/play-back.svg" alt="voltar">
        </button>
    
        <button class="play" v-if="!isPlaying" >
          <img src="../assets/play.svg" @click="play" alt="voltar">
        </button>

        <button class="pause" v-if="isPlaying" >
          <img src="../assets/pause.svg" @click="play" alt="voltar">
        </button>
    
        <button class="next" @click="next">
          <img src="../assets/play-back.svg" alt="voltar">
        </button>
      </div>
      
      <!-- PROGRESS -->
      <input 
        type="range" 
        class="progress"
        step="0.1" 
        min="0" 
        :max="player.duration" 
        :value="currentTimeTeste"
        @change="teste" 
      />
      
      <!-- DURATION -->
      <div v-if="player.src !== ''" class="duration">
        <span >{{Math.floor(player.duration / 60)}}:{{Math.floor(player.duration % 60)}}</span>
  
        <span>{{Math.floor(currentTimeTeste / 60)}}:{{Math.floor(currentTimeTeste % 60)}}</span>
      </div>
    </div>

  </div>
</template>

<script>
import {musics} from '../../music-scheme';

  export default {
    name: "MP3",
    data() {
      return {
        current: {},
        index: 0,
        musics: musics,
        amount: musics.length,
        player: new Audio(),
        isPlaying: false,
        currentTimeTeste: 0
      }
    },
    created() {
      this.current = this.musics[0];
    },
    methods: {
      async next() {
        if(this.index < this.amount - 1) {
          this.index++;
          this.current = this.musics[this.index]
          
          if(this.player.src !== '') {

            this.player.src = this.current.src;
            this.player.play();
          }
        }
      },
      async back() {
        if(this.index !== 0) {
          this.index--;
          this.current = this.musics[this.index];

          if(this.player.src !== '') {
            this.player.src = this.current.src;
            this.player.play();
          }
        }
      },
      async play() {
        if(this.player.src === ""){
          this.player.src = this.current.src
          await this.player.play();
          this.isPlaying = true;
        } else {
          if(!this.player.paused) {
            this.player.pause();
            this.isPlaying = false;
          } else {
            this.player.play();
            this.isPlaying = true;
          }
        }
      },
      async teste(input) {
        this.player.pause()
        console.log(input.target.value)
        console.log(this.player.currentTime)
        this.player.currentTime = input.target.value
        await this.player.play()

      },
      async timeupdate() {
        this.currentTimeTeste = this.player.currentTime;
      }
    },
    mounted() {
      this.player.addEventListener('timeupdate', this.timeupdate, false)
    }

}
</script>

<style>
  .container {
    width: 266px;
    min-height: 498px;
    background-color: #242141;
    padding: 38px;
    border-radius: 12px;

    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 28px;
  }

  .music-info {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 8px;
  }

  .music-info h1 {
    font-weight: 700;
    font-size: 24px;
    color: #e1e1e6;
  }

  .music-info h3 {
    font-weight: 400;
    font-size: 18px;
    color: rgba(225, 225, 230, .65);
  }

  .cover {
    width: 189px;
    height: 189px;
  }

  .cover img {
    width: 100%;
    object-fit: cover;
    border-radius: 8px;
  }

  .options {
    width: 100%;
    display: flex;
    flex-direction: column;
  }

  .controls {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .pause img {
    width: 20px;
    height: 20px;
  }
  .back, .next, .play, .pause {
    outline: none;
  }

  .back:hover, .next:hover, .play:hover, .pause:hover {
    opacity: .6;
    outline: none;
  }

  .next  {
    rotate: 180deg;
  }

  .progress {
    overflow: hidden;
    -webkit-appearance: none;
    appearance: none;
    width: 100%;
    height: 10px;
    border-radius: 8px;
    background-color: rgba(217,217,217,.3);
    margin-top: 2rem;
    margin-bottom: .5rem;
  }

  .progress::-webkit-slider-thumb {
    -webkit-appearance: none;
    height: 10px;
    width: 10px;
    border-radius: 50%;
    background: #f9f9f9;
    cursor: poiter;
    box-shadow: -99px 0 0 95px #fafafa;

    transition: background .3s ease-in-out;
  }
  
  .duration {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding-bottom: 1rem;
  }

  .duration span {
    color: #C4C4CC;
    opacity: .7;
  }
</style>