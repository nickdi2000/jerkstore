


<template>

<div class="container">
    <div class="center">

        <p>Question {{question_no}}</p>
        <img src="https://beta.triviarat.com/images/host.png" class="hostImage">

    </div>
</div>

</template>

<script>

import Vue from 'vue'

export default {
    name: 'Main',
    data: {
        question_no: 'hellllddd'
    },
    beforeCreate() {
        console.log('hello');
    }
}

</script>
