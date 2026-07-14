<script setup>
import { computed, ref } from 'vue';
const nombre = ref('');
const email = ref('');
const edad = ref(null);
const taller = ref('');
const modalidad = ref('online');
const intereses = ref([]);
const comentario = ref('');
const aceptaTerminos = ref(false);
const emailValido = computed(() => /^[^@]+@[^@]+\.[^@]+$/.test(email.value));
const formularioValido = computed(() =>
  nombre.value !== '' && emailValido.value &&
  taller.value !== '' && aceptaTerminos.value
);
const jsonPreview = computed(() => JSON.stringify({
        nombre: nombre.value,
        email: email.value,
        edad: edad.value,
        taller: taller.value,
        modalidad: modalidad.value,
        intereses: intereses.value,
        comentario: comentario.value,
        aceptaTerminos: aceptaTerminos.value
      }, null, 2))
const enviado = ref(false)
function enviar() {
  if (!formularioValido) return;
  enviado.value = true;
}
</script>
<template>
  <h4>▶ Formulario en vivo</h4>
  <form @submit.prevent="enviar">
    <div class="row">
      <div>
        <label>Nombre completo *</label>
        <input type="text" v-model.trim="nombre" placeholder="Tu nombre">
      </div>
      <div>
        <label>Email *</label>
        <input type="email" v-model.trim="email" placeholder="tucorreo@mail.com">
        <div v-if="email && !emailValido" style="color:#dc2626;font-size:.8rem;"> Email inválido</div>
      </div>
      <div>
        <label>Edad *</label>
        <input type="text" v-model.number="edad" placeholder="18">
      </div>

    </div>
    <label>Taller * (select)</label>
    <select v-model="taller">
      <option disabled value="">Selecciona un taller</option>
      <option value="vue">Vue.js desde cero</option>
      <option value="react">React avanzado</option>
      <option value="node">Node & APIs REST</option>
    </select>

    <label>Modalidad (radio)</label>
    <div class="radios">
      <label><input type="radio" v-model="modalidad" value="online"> Online</label>
      <label><input type="radio" v-model="modalidad" value="presencial"> Presencial</label>
      <label><input type="radio" v-model="modalidad" value="hibrido"> Híbrido</label>
    </div>
    <label style="margin-top:.7rem;">Temas de interés (checkbox array)</label>
    <div class="checks">
      <label><input type="checkbox" v-model="intereses" value="frontend"> Frontend</label>
      <label><input type="checkbox" v-model="intereses" value="backend"> Backend</label>
      <label><input type="checkbox" v-model="intereses" value="testing"> Testing</label>
      <label><input type="checkbox" v-model="intereses" value="devops"> DevOps</label>
    </div>
    <label style="margin-top:.7rem;">Comentario (textarea)</label>
    <textarea v-model.trim="comentario" rows="3" placeholder="¿Qué esperas del taller?"></textarea>

    <div class="checks" style="margin-top:.7rem;">
      <label><input type="checkbox" v-model="aceptaTerminos"> Acepto los términos y condiciones *</label>
    </div>
    <button class="btn" type="submit" :disabled="!formularioValido" style="margin-top:1rem;">
      {{ formularioValido ? 'Enviar inscripción ✔' : 'Completa los campos obligatorios (*)' }}
    </button>
    <div v-if="enviado"
      style="background:#dcfce7;color:#166534;padding:.8rem;border-radius:8px;margin-top:1rem;font-weight:600;">
      ✅ ¡Inscripción enviada, {{ nombre }}! Revisa el JSON abajo.
    </div>
    <label style="margin-top:1rem;">📦 Datos que se enviarían (preview reactivo):</label>
      <pre style="background:#0f172a;color:#86efac;">{{ jsonPreview }}</pre>
  </form>

</template>
