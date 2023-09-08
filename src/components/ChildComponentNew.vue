<template>
    <div class="boxContainer"  v-for="(number, index) in boxCount" :key="index">
        <div class="box" v-if="number==0" style="background-color: white;">
            <p class="numberContainer" ></p>
        </div>
        <div class="box" v-if="number==1" style="background-color: black;">
            <p class="numberContainer"></p>
        </div>
    </div>
</template>
<script>
export default {
    props: {
        loaderBoxCount: Number
    },
    data() {
        return { 
            boxCount: [...Array(this.loaderBoxCount).keys() ]|| 0,
            color:'white',
        }
    },
    methods: {
        sleep(ms) {
            return new Promise(resolve => setTimeout(resolve, ms));
        },
        async renderIterator() {
                for(let i =1; i < this.boxCount.length; i++){
                    this.boxCount.fill(0);
                    this.boxCount[i] = 1;
                    this.currentBoxColor = 'black';
                    await this.sleep(1000);
                }
                this.renderIterator();
        },
    },
   mounted() {
    this.renderIterator();
   }
}  
</script>
<style scoped>
.box {
  width: 15%;
  margin:auto;
  border: 1px solid grey;
}

.boxContainer{
    display: flex;
    justify-content: flex-end;
}
</style>
