
<template>
<div>
  {{msg}}
  My Example {{counter}}
  <button @click="increase">
    +
  </button>
  <button @click="decrease">
    -
  </button>
{{times}}

 <span v-if="seen">Now you see me</span>
 <span v-else>click the button to see more</span>
 <button @click="seen=!seen">Enable span</button>
<p v-bind:style="{color:'blue'}">
list:
</p>
<ol>
<li v-for="fruit in listItems">
{{fruit}}
</li>
</ol>
<ExampleChild :items="currentItem"/>
<button @click="show = !show">Toggle show</button>
<transition name="bounce">
   <p v-if="show">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris facilisis enim libero, at lacinia diam fermentum id. Pellentesque habitant morbi tristique senectus et netus.</p>
 </transition>
</div>
</template>

<script>
import ExampleChild from './ExampleChild'
export default {
name: "Example",
props: ['msg'],
data(){                       //state
  return {
    counter: 1,
    seen: false,
    listItems: ['apple','banana','watermaloon','peach'],
    currentItem:'banana',
    show:true
  }
},
methods: {                 //method binding and declaration
increase(){
this.counter+=1
},
decrease(){
  this.counter-=1
}
},
computed:{
  times(){
    return this.counter*10 //immutable and reactive (when counter changes times changes) variable no no side effect(we can't change the state inside)
  },
},
components:{
  ExampleChild
}

}
</script>

<style scoped>
button{
background-color: red;

}
.bounce-enter-active {
  animation: bounce-in .5s;
}
.bounce-leave-active {
  animation: bounce-in .5s reverse;
}

@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
</style>
