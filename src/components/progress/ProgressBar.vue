<template>
       <div class="bg-gray-200 h-4 rounded-full w-full">
            <div class="progress" :style="`width: ${progress}%;`">
            </div>
       </div>
</template>

<script setup lang="ts">
const {progress=0} = defineProps({
    progress: Number
})
</script>

<style scoped>
@keyframes progress {
    0%{
        @apply bg-red-400;
    }
    50%{
        @apply bg-purple-400;
    }
    75%{
        @apply bg-indigo-400;
    }
    100%{
        @apply bg-green-400;
    }
}

@-webkit-keyframes progress {
    0%{
        @apply bg-red-400;
    }
    50%{
        @apply bg-purple-400;
    }
    75%{
        @apply bg-indigo-400;
    }
    100%{
        @apply bg-green-400;
    }
}


.progress{
    @apply h-full rounded-full transition-all ease-in-out duration-150;
    animation: progress 2s infinite linear;
}


</style>