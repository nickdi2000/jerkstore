<style scoped>

.box {
    z-index: 10;
    border-width: 5px;
    border-radius: 25px;
    padding: 25px;
    box-shadow: 10px 10px 8px #000;
    width: 100%;
    font-size: 2em;
}

body{
  opacity: 0;
  background-color: yellow;
}

.host {
    width: 130px;
    height: auto;
    float: right;
}

.answers{
  color: white;
  background-color: red;
  padding: 12px;
  border-radius: 25px;

}

</style>
<template>

<div class="container" id="main">

    <div class="row">
        <h2>Question #{{question_no + 1}}</h2>
        <br/>
        <p class="text-danger" v-if="question_no == (length-1)" style="line-hight:20px;">Last question</p>
    </div>
    <div class="row">
        <div class="col-lg-12">
            <div class="box">
                {{questions[question_no].question}}
                <br/>
                <p class="answers" v-if="showAnswers">{{questions[question_no].answer}}</p>
                <img :src="images.host.src" class="host">
            </div>

              <br/>
            <div class="buttons">
              <button class="btn btn-lg btn-info" v-on:click="goTo(-1)"><</button> &nbsp;
              <button class="btn btn-lg btn-info" v-on:click="goTo(1)">></button>
            </div>
            <br/>
        </div>
      </div>

                <!--
                <br/><br/>

                <p style="line-height: 0px;">Play Along at:</p>
                <h3>TriviaRat.com/JERK</h3>
                <img :src="images.qr.src">
                -->
</div>

</template>

<script>

import json from './questions.json'
import images_json from './images.json'
import VideoBg from 'vue-videobg'


export default {
    name: 'Main',
    data: function() {
        return {
            question_no: 0,
            length: Object.keys(json).length,
            questions: json,
            images: images_json,
            showAnswers: false,
        }
    },
    components: { VideoBg },

    methods: {
      goTo: function(i){
      //if not null, then increment/decrement
        if(this.questions[this.question_no + i]){
          this.question_no += i
        };
      }
    },
    created() {
        window.addEventListener('keydown', (e) => {
            if (e.keyCode == 39) {
                this.goTo(1);
            }
            if (e.keyCode == 37) {
                this.goTo(-1);
            }
            if(e.key == 'Escape'){
              this.showAnswers = !this.showAnswers;
            }
        });
    },
}

</script>
