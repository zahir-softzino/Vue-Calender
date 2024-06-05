<template>
    <ul>
        <li class="flex justify-between" v-for="(hero, index) in dcHeros" :key="index">
            <div>
            {{ hero.name }}
            </div>
            <button @click="remove(index)">x</button>
        </li>
    </ul>
</template>

<script>
export default {

    data(){
        return{
        isActive: false,
        newHero: "",
        dcHeros:[
            {name: 'SuperMan'},
            {name: 'SuperGirl'},
            {name: 'Flash'},
            {name: 'Arrow'},
            {name: 'BatMan'},
        ],
        // heroCount : this.dcHeros.length
        }
    },
    methods:{
        addHero(){
        if(this.newHero !== ''){
            this.dcHeros.push({name: this.newHero});
            this.newHero = '';
        }
        },
        remove(index){
        this.dcHeros = this.dcHeros.filter((hero,i) => i != index)
        }
    },
    computed:{
        heroCount(){
        return this.dcHeros.length;
        }
    }

}
</script>

<style>

</style>