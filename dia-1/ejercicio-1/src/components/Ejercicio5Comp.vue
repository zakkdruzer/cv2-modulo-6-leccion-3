<script setup>
    import {computed, ref} from 'vue';
    const mayorEdad = ref(false);
    const canales= ref([]);
    const tema=ref('claro');
</script>
<template>
     <h4>1) Booleano</h4>
     <div class="checks">
        <label><input type="checkbox" v-model="mayorEdad"> Confirmo que soy mayor de edad</label>
      </div>
      <div class="out">mayorEdad: <b>{{ mayorEdad }}</b> ({{ typeof mayorEdad }})</div>
     <hr class="soft" />
      <h4>2) Múltiple → array</h4>
      <div class="checks">
        <label><input type="checkbox" v-model="canales" value="email"> Email</label>
        <label><input type="checkbox" v-model="canales" value="sms"> SMS</label>
        <label><input type="checkbox" v-model="canales" value="push"> Push</label>
        <label><input type="checkbox" v-model="canales" value="whatsapp"> WhatsApp</label>
      </div>
      <div class="out">canales: <b>{{ canales }}</b><br>total seleccionados: <b>{{ canales.length }}</b></div>
      <hr class="soft" />
      <h4>3) Valores personalizados (:true-value / :false-value)</h4>
      <div class="checks">
        <label><input type="checkbox" 
                      v-model="tema" 
                      :true-value="'oscuro'" 
                      :false-value="'claro'"> Activar modo oscuro</label>
      </div>
      <div class="out">tema: <b>{{ tema }}</b> (no es true/false, es un string 😉)</div>
</template>

