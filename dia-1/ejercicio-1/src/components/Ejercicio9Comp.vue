<script setup>
import { computed, ref } from 'vue';
const tamano = ref('mediana');
const masa = ref('tradicional');
const ingredientes = ref([]);
const cantidad = ref(1);
const instrucciones = ref('');
const empaque = ref('normal');
const precioBase = { pequena: 6000, mediana: 8500, familiar: 12000 };
const precioIngrediente = 900;

const total = computed(() => {
  const base = precioBase[tamano.value] || 0;
  const extras = ingredientes.value.length * precioIngrediente;
  const regalo = empaque.value === 'regalo' ? 1500 : 0;
  const cant = cantidad.value > 0 ? cantidad.value : 0;
  return (base + extras + regalo) * cant;
});


</script>
<template>
  <h4>▶ Configurador en vivo</h4>
  <div class="row">
    <div>
      <label> Tamaño (select)</label>
      <select v-model="tamano">
        <option value="pequena">Pequeña — $6.000</option>
        <option value="mediana">Mediana — $8.500</option>
        <option value="familiar">Familiar — $12.000</option>
      </select>
    </div>
    <div>
      <label>Cantidad (input.number)</label>
      <input type="number" min="1" v-model.number="cantidad" />
    </div>
    <label>Tipo de masa (radio)</label>
    <div class="radios">
      <label><input type="radio" v-model="masa" value="tradicional"> Tradicional</label>
      <label><input type="radio" v-model="masa" value="delgada"> Delgada</label>
      <label><input type="radio" v-model="masa" value="integral"> Integral</label>
    </div>
    <label style="margin-top:.7rem;">Ingredientes extra — $900 c/u (checkbox array)</label>
    <div class="checks">
      <label><input type="checkbox" v-model="ingredientes" value="Champiñón"> Champiñón</label>
      <label><input type="checkbox" v-model="ingredientes" value="Pepperoni"> Pepperoni</label>
      <label><input type="checkbox" v-model="ingredientes" value="Choclo"> Choclo</label>
      <label><input type="checkbox" v-model="ingredientes" value="Aceituna"> Aceituna</label>
      <label><input type="checkbox" v-model="ingredientes" value="Tocino"> Tocino</label>
    </div>
    <label style="margin-top:.7rem;">Instrucciones (textarea)</label>
    <textarea v-model.trim="instrucciones" rows="2" placeholder="Ej: sin cebolla, cortar en 8..."></textarea>
    <div class="checks" style="margin-top:.7rem;">
      <label><input type="checkbox" v-model="empaque" :true-value="'regalo'" :false-value="'normal'"> Empaque de regalo
        (+$1.500)</label>
    </div>
    <hr class="soft" />
    <div style="display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:1rem;">
      <div>
        <div>Pizza <b>{{ tamano }}</b>, masa <b>{{ masa }}</b> ×{{ cantidad }}</div>
        <div class="muted-txt">
          Ingredientes:
          <span v-if="ingredientes.length === 0">solo queso 🧀</span>
          <span v-for="ing in ingredientes" :key="ing" class="pill">{{ ing }}</span>
        </div>
        <div class="muted-txt">Empaque: {{ empaque }}</div>
      </div>
      <div class="price">${{ total.toLocaleString('es-CL') }}</div>
    </div>
    <button class="btn" :disabled="cantidad < 1" style="margin-top:1rem;">
      {{ cantidad < 1 ? 'Elige al menos 1 pizza' : `Pedir por $${total.toLocaleString('es-CL')} 🍕` }} 
    </button>
  </div>

</template>
