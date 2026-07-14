<script setup>
    import {ref} from 'vue';
    const nombre= ref('Jorge');
    const colorFondo= ref('#e0f2fe');
    const colorAvatar= ref('#42b883');
    const avatarText=nombre.value.charAt(0).toUpperCase() || '?'

</script>
<template>
     <div class="row">
        <div>
          <label>Nombre</label>
          <input type="text" v-model="nombre" placeholder="Escribe un nombre" />
        </div>
        <div>
          <label>Color de fondo</label>
          <input type="color" v-model="colorFondo" style="width:60px;height:40px;border:none;background:none;" />
        </div>
        <div>
          <label>Color del avatar</label>
          <input type="color" v-model="colorAvatar" style="width:60px;height:40px;border:none;background:none;" />
        </div>
      </div>
    <div class="card-preview" :style="{background: colorFondo}">
        <div class="avatar" :style="{background: colorAvatar}">{{ avatarText }}</div>
        <div>
            <strong>{{ nombre || 'Sin Nombre' }}</strong>
        </div>
    </div>
</template>



<style scoped>

</style>