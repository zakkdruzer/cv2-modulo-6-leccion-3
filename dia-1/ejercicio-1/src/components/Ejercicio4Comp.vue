<script setup>
    import {computed, ref} from 'vue';
   
    const LIMITE= 20;
    const texto=ref('');
    const restantes = computed(()=> LIMITE - texto.value.length);
    const excedido = computed(()=> restantes.value < 0);

</script>
<template>
 <textarea v-model="texto" row="4" placeholder="Línea 1&#10;Línea 2...">

 </textarea>
 <div class="char-counter" :style="{ color: excedido ? '#dc2626' : '#64748b' }">
      {{ restantes }} caracteres restantes {{ excedido ? '⚠ te pasaste' : '' }}
 </div> 

<!-- <div v-if="excedido" class="char-counter"  style="color: #dc2626">
   ⚠ te pasaste       
 </div>
<div v-else class="char-counter">
     {{ restantes }} caracteres restantes 
</div> -->

  <pre style="background:#0f172a; color:#86efac;">{{ texto || '(vacío)' }}</pre>
</template>

