<script setup>
import {ref} from 'vue'
const messageText = ref('je suis un message');
const messageList = ref([])

function addMessage(){
    if(! messageText.value){
        return;
    }

    messageList.value.push(messageText.value);
    messageText.value = '';
}

</script>

<template>
    <div v-for="(message, index) in messageList" class="p-4" :key="index">
        {{ message }}
    </div>
    <div class="flex align-center">
        <textarea v-model="messageText" name="message" id="message" rows="1" class="text-black rounded-md"></textarea>
        <button v-on:click="addMessage" class="p-2 bg-blue-600 rounded-md ml-3">Envoyer</button>
    </div>
</template>