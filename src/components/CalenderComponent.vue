<template>
  <div class="m-auto mx-20">
    <section class="mx-2 text-center mt-10 mb-5">
        <h2 class="font-bold text-2xl">{{ currentMonthName }} {{ currentYear }}</h2>
    </section>
    <section class="flex">
        <p class="text-center my-4" style="width: 14.28%;" v-for="day in days" :key="day">{{ day }}</p>
    </section>
    <section class="flex flex-wrap">
        <p class="text-center my-4" style="width: 14.28%;" v-for="num in startDay()" :key="num"></p>
        <p class="text-center my-4" style="width: 14.28%;" v-for="num in daysInMonth()" :key="num" :class="currentDateClass(num)">{{ num }}</p>
    </section>
    <section class="flex justify-between mx-10">
        <button class="px-5 border rounded" @click="previous">Prev</button>
        <button class="px-5 border rounded" @click="next">Next</button>
    </section>
  
  </div>
</template>

<script>
export default {
    data(){
        return{
            currentDate: new Date().getUTCDate(), 
            currentMonth: new Date().getMonth(),
            currentYear: new Date().getFullYear(),
            days: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat']

        }
    },
    methods:{
        daysInMonth(){
            return new Date(this.currentYear , this.currentMonth+1, 0).getDate();
        },
        startDay(){
            return new Date(this.currentYear, this.currentMonth, 1).getDay();
        },
        next(){
            if(this.currentMonth === 11){
                this.currentMonth = 0;
                this.currentYear++;
            }
            else{
                this.currentMonth++;

            }
        },
        previous(){
            if(this.currentMonth === 0){
                this.currentMonth = 11;
                this.currentYear--;
            }
            else{
                this.currentMonth--;

            }
        },
        currentDateClass(num){

            const calenderFullDate = new Date(this.currentYear, this.currentMonth, num).toDateString();
            const currentFullDate = new Date().toDateString();

            return calenderFullDate === currentFullDate ? "text-yellow-500 border bg-green-900": "";
        }
    },
    computed:{
        currentMonthName(){
            return new Date(this.currentYear, this.currentMonth).toLocaleString('default',{month:'long'})
        }
    }
}
</script>

<style>

</style>