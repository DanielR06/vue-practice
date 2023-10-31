<script setup>
    import { ref, computed } from 'vue';
    const array = ref([]);
    const counter = ref(0);
    const classCounter = computed(() =>{
    if(counter.value > 0){
      return 'positive';
    }else if(counter.value < 0){
      return 'negative';
    } else{
    return 'zero';
}
})
    const blockBtn = computed(() =>{
        const inside = array.value.includes(counter.value);
        return inside ? true : false;
    })
    const increase = () => {
        counter.value++; 
    };
    const decrease = () => {
        counter.value--;
    }
    const reset = () => {
        counter.value = 0;
    }
    const add = () => {
        array.value.push(counter.value);
    }
</script>
<template>
    <div style="border: 1px solid">
        <p>counter</p>
        <p :class="`counter ${classCounter}`" >{{ counter }}</p>
        <button @click="increase">Increase</button>
        <button @click="decrease">Decrease</button>
        <button @click="reset">Reset</button>
        <button @click="add" :disabled="blockBtn"> Add</button>
        <ul>
            <li v-for="number in array">{{ number }}</li>
        </ul>
    </div>
</template>
<style></style>