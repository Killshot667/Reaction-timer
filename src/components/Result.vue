<template>

<p>Your reaction time is {{score}} ms</p>
<p class="level">{{level}}</p>

  
</template>

<script>
export default {
    props : ["score"],
    data(){
        return {
            level : "default",
        }
    },
    mounted(){
        if(this.score <= 400)
        {
            this.level = "Holy shit , you fast as hell!!";
        }
        else if(this.score <= 700)
        {
            this.level = "Those fingers be killing it yo!";
        }
        else if(this.score <= 900)
        {
            this.level = "Meh. You are descently fast";
        }
        else if(this.score <= 1200)
        {
            this.level = "My grandma is faster than you";
        }
        else 
        {
            this.level = "Tum to chod hi do beta. Tumse nai hoga";
        }
        console.log(this.level);

    }

}
</script>

<style>
.level {
    font-size: 1.4rem;
    font-weight: bold;
    color: darkgreen;
}

</style>