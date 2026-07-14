<script setup>
    import {ref} from 'vue';
    const cuenta= ref(20000);
    const propinaPct= ref(10);
    const propina= ref(Math.round(cuenta.value * propinaPct.value / 100));
    const total=ref(cuenta.value + propina.value);
    const local= ref('');
    const email= ref('');


    

</script>
<template>
  <div class="row">
      
        <div>
          <label>Monto de la cuenta ($)</label>
          <input type="number" v-model.number="cuenta" />
        </div>
        <div>
          <label>Propina (%)</label>
          <input type="number" v-model.number="propinaPct" />
        </div>
        <div>
          <label>Nombre del local (.trim)</label>
          <input type="text" v-model.trim="local" placeholder="  Café Central  " />
        </div>
        <div>
          <label>Email (.lazy)</label>
          <input type="text" v-model.lazy="email" placeholder="Su EMail" />
        </div>
      </div>
      <div>
        Local: "<b>{{ local || '—' }}</b>" (largo real: {{ local.length }})<br>
        Email: "<b>{{ email || '—' }}</b>" (largo real: {{ email.length }})<br>
        Propina: <b>${{ propina.toLocaleString('es-CL') }}</b><br>
        Total a pagar: <b>${{ total.toLocaleString('es-CL') }}</b><br>
        Tipo de dato de "cuenta": <b>{{ typeof cuenta }}</b> ✔ (gracias a .number)
      </div>

</template>

