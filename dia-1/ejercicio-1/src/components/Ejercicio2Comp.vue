<script setup>
    import {ref} from 'vue';
 
    const mensaje= ref('Hola Alumnos');

    const frasesLoremIpsum = [
  "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
  "Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
  "Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris.",
  "Duis aute irure dolor in reprehenderit in voluptate velit esse cillum.",
  "Excepteur sint occaecat cupidatat non proident, sunt in culpa qui.",
  "Curabitur pretium tincidunt lacus, nulla gravida orci a odio.",
  "Nullam varius, turpis et commodo pharetra, est eros bibendum elit.",
  "Integer in mauris eu nibh euismod gravida, pellentesque eu enim.",
  "Duis ac tellus et risus vulputate vehicula, donec lobortis risus.",
  "Aliquam erat volutpat, phasellus pede arcu, dapibus aliquet mattis.",
  "Phasellus rhoncus, tellus vitae mattis varius, ipsum ipsum laoreet.",
  "Praesent dapibus, neque id cursus faucibus, tortor neque egestas.",
  "Aliquam erat volutpat, nam dui mi, tincidunt quis, accumsan porttitor.",
  "Pellentesque habitant morbi tristique senectus et netus et malesuada.",
  "Fusce pellentesque suscipit nibh, suspendisse commodo tempus lectus."
];
  // const index=ref(0);
  //   setInterval(()=>{
  //     mensaje.value=frasesLoremIpsum[index.value]
  //     index.value++
  //     if(index.value==15)index.value=0;
  //   },1000)
</script>
<template>
    <input v-model="mensaje" placeholder="Escriba algo..."/>
    <p>En vivo: {{ mensaje }}</p>
    <p>Al Revés: {{ mensaje.split('').reverse().join('')}}</p>
    <p>Largo: {{ mensaje.length }}</p>
</template>

