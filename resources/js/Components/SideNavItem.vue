<script setup >

import { defineProps, toRef } from 'vue';

import Home from 'vue-material-design-icons/Home.vue'
import FolderPlayOutline from 'vue-material-design-icons/FolderPlayOutline.vue';
import ImageMultiple from 'vue-material-design-icons/ImageMultiple.vue';
import ThumbDownOutline from 'vue-material-design-icons/ThumbDownOutline.vue';
import History from 'vue-material-design-icons/History.vue';
import ClockOutline from 'vue-material-design-icons/ClockOutline.vue';
import VideoPluslineIcon from 'vue-material-design-icons/VideoPlusOutline.vue';
import DeletaIcon from 'vue-material-design-icons/Delete.vue';


const props = defineProps({
    openSideNav: Boolean,
    iconString: String,
})
const { openSideNav, iconString } = toRef(props)

let icon = null

if (iconString.value === 'Home') icon = Home
if (iconString.value === 'Subscriptions') icon = FolderPlayOutline
if (iconString.value === 'Library') icon = ImageMultiple
if (iconString.value === 'Liked') icon = ThumbDownOutline
if (iconString.value === 'History') icon = History
if (iconString.value === 'Watch Later') icon = ClockOutline
if (iconString.value === 'Add Video') icon = VideoPluslineIcon
if (iconString.value === 'DeletaIcon') icon = DeletaIcon



</script>


<template>
    <li 
    :class="[!openSideNav ? 'p-2': 'flex items-center p-2']"
    class="text-white text-sm font-semibold text-center hover:bg-gray-700 rounded-lg cursor-pointer"
    >
       <div :class="[!openSideNav ? 'w-full flex justify-center': '']">
        <component :is="icon"></component>
       </div>
       <div :class="[!openSideNav ? ' ': 'mt-1 ml-4']">
        <span v-if="!openSideNav">{{ iconString.substring(0,4) }}</span>
        <span v-else>{{ iconString }}</span>
       </div>
    </li>
</template>




