<script setup>
    import {computed, ref} from 'vue';
     const comunasPorRegion = {
        'Metropolitana': ['Santiago', 'Providencia', 'Maipú', 'La Florida', 'Puente Alto'],
        'Valparaíso': ['Valparaíso', 'Viña del Mar', 'Quilpué', 'Villa Alemana'],
        'Biobío': ['Concepción', 'Talcahuano', 'Chiguayante', 'Coronel']
      }
      const region = ref('')
      const comuna = ref('')
      const comunas = computed(() => comunasPorRegion[region.value] || [])
</script>
<template>
    <h4>▶ Demo en vivo</h4>
    <div class="row">
        <div>
          <label>Región</label>
          <select v-model="region">
            <option disabled value="">Elige región</option>
            <option v-for="r in Object.keys(comunasPorRegion)" :key="r" :value="r">{{ r }}</option>
          </select>
        </div>
        <div>
          <label>Comuna</label>
          <select v-model="comuna" :disabled="!region">
            <option disabled value="">{{ region ? 'Elige comuna' : 'Primero elige región' }}</option>
            <option v-for="c in comunas" :key="c" :value="c">{{ c }}</option>
          </select>
        </div>
      </div>
      <div class="out">
        Región: <b>{{ region || '—' }}</b> · Comuna: <b>{{ comuna || '—' }}</b>
      </div>
</template>

