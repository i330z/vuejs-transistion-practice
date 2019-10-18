<template>
  <div class="container">
    <div class="row">
      <div class="col-md-12">
        HEllp
        <div class="btn btn-primary" @click="show = !show">
          Click Here
        </div>
        <transition name="fade">
          <div class="alert alert-info" v-if="show">this is an alert</div>
        </transition>

      
      <button class="btn btn-primary" @click="addItem">Add Number</button>
      <ul class="list-group">
      <transition-group name="slide" >

        <li class="list-group-item"
         v-for="(number, index) in numbers" 
         :key="number"
         @click="removeItem" 
         style="cursor:pointer">
         {{ number }}</li>
      </transition-group>
      </ul>

      </div>

    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      show: false,
      numbers:[1,2,3,4,5,6]
    }
  },
  methods:{
    addItem() {
      const pos = Math.floor(Math.random() * this.numbers.length);
      this.numbers.splice(pos, 0, this.numbers.length + 1);
    },
    removeItem(index){
      this.numbers.splice(index,1);
    }
  }
 
}
</script>


<style>
  .fade-enter{
    opacity: 0;
  }
  .fade-enter-to{
    transition: opacity 1s;
  }
  .fade-leave{

  }
  .fade-leave-to{
    transition: opacity 1s;
    opacity: 0;
  }

  .slide-enter{
    opacity: 0;
  }
  .slide-enter-active{
    animation: slide-in 1s ease-in forwards;
    transition: opacity 1s;
  }
  .slide-leave{
     
  }

  .slide-leave-active{
    animation: slide-out 1s ease-out forwards;
    transition: opacity 1s;
    opacity: 0;
    position: absolute;
  }
  .slide-move{
    transition: transform 1s;
  }

  @keyframes slide-in{
    from{
      transform: translateY(20px);
    }
    to{
      transform: translateY(0);
    }
  }

  @keyframes slide-out {
    from{
      transform: translateY(0)
    }
    to{
      transform: translateY(-20px)
    }
  }
</style>