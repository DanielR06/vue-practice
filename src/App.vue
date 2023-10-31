<script setup>
import Counter from './components/Counter.vue'
import { ref, computed } from 'vue';

const active = ref(true);

  const name = 'Daniel';
  const fontColor = "color: blue";
  const show = true;
  const fruits = [
        {
            name: "Apple",
            price: "$1.00",
            description: "A Apple",
            stock: 0
        },
        {
            name: "Pear",
            price: "$2.00",
            description: "A pear",
            stock: 10
        },
        {
            name: "Orange",
            price: "$3.00",
            description: "A orange",
            stock: 20
        },
    ];
  const fruitObject = {
    name: "Golden Apple",
    price: "$100",
    description: 'A one comun Golden Apple'
  }
  const handleClick = (message) => {
    console.log(message);
  }
  const changeState = () => {
    if(active.value == true){
      active.value = false;
    }else{
      active.value = true;
    }
    
  };
  
  
</script>

<template>
  <h1>Hello {{name.toUpperCase()}}</h1>
  <p v-bind:style="fontColor" >It is a single page with vuejs</p>
  <h2>{{ active ? 'Is active' : 'No active' }}</h2>
  <p v-if="!active" >Here i am</p>
  <p v-else >here i am not</p>
  <h3 v-show="show">show or display none</h3>
  <button @click="changeState" >Change</button>
  <ul>
    <li v-for="(fruit, index) in fruits"
    :key="fruit.name"    
    >
    {{index}} - {{ fruit.description }} {{ fruit.price }}
  </li>
</ul>
<ul style="color: yellow">
  <li
  v-for="(value, property, index) in fruitObject"
  :key="value" 
  >
  {{index}} - {{property}}: {{ value }}
</li>
</ul>
<ul>
  <template v-for="item in fruits" :key="item.name">
    <li v-if="item.stock >= 10">
      {{ item.stock }}
    </li>
  </template>
</ul>
<button  v-on:click.left.prevent="handleClick('Click Left')">Left</button>
<button  @click.middle="handleClick('Click Middle')">Middle</button>
<button  @click.right="handleClick('Click Right')">Right</button>

<Counter>

</Counter>
</template>

<style>
h1{
  color: blueviolet;
}
.counter{
  font-size: 40px;
}
.zero{
  color: inherit;
}
.positive{
  color: green;
}
.negative{
  color: red;
}
</style>