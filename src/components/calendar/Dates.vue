<template>
    <div class="w-full bg-gray-200 p-3 rounded-b-md">
        <div class="grid grid-cols-7 place-items-center gap-x-2 gap-y-4">
            <div v-for="day in days" :key="day">
                <span class="text-gray-500 font-semibold">{{ day.substr(0,3) }}</span>
            </div>

            <template v-for="(d, index) in dates" :key="d">

                <template v-if="index == 0">
                    <div v-for="i in d.day" :key="i" >
                    </div>
                </template>

                <button class="w-9 h-9 rounded-full flex items-center justify-center text-sm font-semibold" 
                 @click="() => selected(d.date)"
                 :class="{
                    'bg-gray-800 text-gray-100': (d.date == dayjs().date() && dateProps.selectedValues.month == dayjs().month() 
                    && dateProps.selectedValues.year == dayjs().year()),
                    'bg-emerald-500 text-gray-50 ring ring-green-700': d.date == date,
                    'bg-gray-300': d.date != date
                 }">
                    <span>
                         {{d.date}}
                    </span>
                </button>

               
            </template>

        </div>
    </div>
</template>

<script setup lang="ts">
import dayjs from "dayjs"
import {watch, onMounted, ref} from "vue"

type SelectedValues = {
    year: number
    month: number
}

type Date = {
    day: number,
    date: number
}


const date = ref<number>(null)


const dateProps = defineProps<{
    selectedValues: SelectedValues
    selectedDate: number
}>()

const dateEmit = defineEmits<{(e: 'selected', v: number):void}>()

const dates = ref<Date[]>([])

onMounted(()=>{
    generateDatesForThatMonth()
})

watch(()=>dateProps.selectedValues, (v)=>{
    date.value = null
    generateDatesForThatMonth(v.month, v.year)
}, {
    deep: true
})

const days = [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday"
]


function generateDatesForThatMonth(m = dayjs().month(), y = dayjs().year())
{
    dates.value = []
    let d = dayjs().month(m).year(y)
    const daysInMonth = d.daysInMonth()
    for( let i = 1; i <= daysInMonth; i++)
    {
        dates.value.push({
            date: i,
            day: d.date(i).day()
        })
    }

    console.log("dates", dates.value)
}

function selected(d){
    date.value = d
    dateEmit('selected', d)
}

</script>

<style scoped>

</style>