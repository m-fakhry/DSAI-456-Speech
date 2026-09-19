<script setup>
import { useSlideContext } from '@slidev/client'
const { $slidev } = useSlideContext()

// Debug output
console.log('BottomBar mounted', {
  title: $slidev.configs.title,
  author: $slidev.configs.author,
  date: $slidev.configs.date
})

defineProps({
  courseTitle: { type: String, required: false },
  courseCode: { type: String, default: "2023" },
  courseInstructor: { type: String, required: false},
  courseYear: { type: String, required: false},
  courseVenue: { type: String, required: false},
})
</script>

<template>
  <div v-if="$slidev.configs.title" class="bg-barBottom flex absolute w-full bottom-0 left-0 py-0.5 px-2 text-sm flex-items-center">
    <div class="grid grid-cols-5 gap-8 h-full pl-2 flex">
     {{ $slidev.configs.author }} 
     <div class="divider"></div> 
     {{ $slidev.configs.title }}
     <div class="divider"></div> 
     {{ $slidev.configs.year }}
     <div class="divider"></div> 
     {{ $slidev.configs.venue }}
     <div class="divider"></div> 
     Lecture {{ $slidev.configs.lecture }}
    </div>    
  </div>
</template>

<style scoped>

.divider {
  width: 1px; /* Width of the divider line */
  height: 1em; /* Height can be adjusted as needed */
  background-color: azure; /* Color of the divider */
  margin: 2px 10px; /* Spacing around the divider */
}

.bg-barBottom {
  background:  hwb(200 33% 5%);
  background-size: 180% 180%;
  opacity: 1.0;
  color:rgb(0, 8, 8);
}

@keyframes gradient-animation {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

</style>
