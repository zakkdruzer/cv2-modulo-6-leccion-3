<script setup>
    import {computed, ref} from 'vue';
    const envio=ref('retiro');
    const costos={ retiro: 0, normal: 3990, express: 7990 };
    const costoEnvio=computed(() => costos[envio.value]);
</script>
<template>
    <h4>▶ Demo en vivo</h4>
    <div class="radios" style="display:flex;flex-direction:column;gap:.5rem;">
        <label><input type="radio" v-model="envio" value="retiro"> Retiro en tienda — Gratis</label>
        <label><input type="radio" v-model="envio" value="normal"> Despacho normal — $3.990</label>
        <label><input type="radio" v-model="envio" value="express"> Express (24h) — $7.990</label>
      </div>
      <div class="out">
        Opción seleccionada: <b>{{ envio }}</b><br>
        Costo de envío: <b>${{ costoEnvio.toLocaleString('es-CL') }}</b>
      </div>
</template>

