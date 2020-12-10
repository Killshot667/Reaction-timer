<template>
  <div class="block" v-if="showBlock" :style="{ margin: margin_t + 'px' + ' ' + margin_l + 'px' }">
      CLICK ME!!
  </div>
</template>

<script>
export default {
    props : ['delay','margin_t','margin_l'],
    data() {
        return{
        showBlock: false,
        }
    },
    mounted(){
        console.log("mounted");
        setTimeout(() => {
            this.showBlock = true;
            console.log(this.delay);

            
        },this.delay)

    }

}
</script>

<style>
.block {
    width:200px;
    border-radius: 10px;
    background: aquamarine;
    text-align: center;
    padding: 50px 0;
    
}

</style>