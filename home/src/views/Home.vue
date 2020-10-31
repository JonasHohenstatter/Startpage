<template>
    <div class="d-flex justify-content-center flex-column">
        <h3 style="margin-top: 6vh">Erstelle hier deine Startseite mit deinem Alter!</h3>
        <h4 style="margin-top: 1vh">Gib hier dein Gebursdatum an: </h4>
        <div class='d-flex flex-row justify-content-center' style='margin-top: 3vh'>
            <div class="dropdown">
                <button class="btn btn-secondary dropdown-toggle"  type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">{{birthdate[0]}}</button>
                <div class="dropdown-menu" aria-labelledby="dropdownMenuButton" style="height: 25vh; overflow-y: scroll">
                    <a v-for="n in 31" class='dropdown-item' :key="n" @click="birthdate[0] = n">{{n}}</a>
                </div>
            </div>
            <div class="dropdown" style='margin-left: 2vw'>
                <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">{{birthdate[1]}}</button>
                <div class="dropdown-menu" aria-labelledby="dropdownMenuButton" style="height: 25vh; overflow-y: scroll">
                    <a class='dropdown-item' v-for="month in months" :key='month' @click="birthdate[1] = month">{{month}}</a>
                </div>
            </div>
            <div class="dropdown" style='margin-left: 2vw'>
                <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">{{birthdate[2]}}</button>
                <div class="dropdown-menu" aria-labelledby="dropdownMenuButton" style="height: 25vh; overflow-y: scroll">
                    <a v-for="n in years" class='dropdown-item' :key="n" @click="birthdate[2] = n">{{n}}</a>
                </div>
            </div>
        </div>
        <span style='margin-top: 8vh; font-size: 3vh'>Dein Custom Link lautet: <a v-bind:href='"https://mystartpage.vercel.app/#/" + changelink'>https://mystartpage.vercel.app/#/{{changelink}}</a></span>
        <div style='margin-top: 2vh; font-size: 3vh'>Du musst diesen Link in den Einstellungen deines Browsers als Standart Startseite einstellen</div>
    </div>
</template>

<script>
export default {
    name: 'Home',
    data(){
        return{
            months: [
                'January',
                'February',
                'March',
                'April',
                'May',
                'June',
                'July',
                'August',
                'September',
                'October',
                'November',
                'December'
            ],
            years: [],
            birthdate: ["Tag", "Monat", "Jahr"]
        }
    },
    mounted(){
        var current = parseInt(new Date().getFullYear())
        for(let i = 1; i <= 100; i++){
            this.years.push(current)
            current = current - 1
        }
    },
    methods:{
        
    },
    computed: {
        changelink: function(){
            return this.birthdate.join('+')
        }
    }
}
</script>

<style>

</style>