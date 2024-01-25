<script setup>
import {computed} from 'vue';

const props = defineProps({
    message: {
        type: Object,
        required: true 
    }
});

function formatDate(date){
    let formattedDay = date.toLocaleDateString();
    let formattedTime = date.toLocaleTimeString('default', {hour: '2-digit', minute: '2-digit'});
    return `${formattedDay} à ${formattedTime}`;
};

const formattedDate = computed(() => {
    const date = props.message.date;
    return formatDate(date);
});

</script>

<template>
    <div class="flex">
        <img class="bg-slate-600 h-10 w-10 rounded-full" :src="message.user.avatarUrl">
        {{ message.user.username }}
        <span class="text-xs text-opacity-40 text-gray-50">
            
            {{ formattedDate }}
            <!--TODO format jj/mm/yyyy à hh:mm -->
            <!-- Aujourd'hui si c'est aujourd'hui -->
            <!-- Hier...-->
        </span>
    </div>

    <div>
        {{ message.text }}
    </div>
</template>