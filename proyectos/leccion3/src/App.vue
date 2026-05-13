
<script setup>
  import { reactive, computed } from 'vue'

  const form = reactive({
    nombre: '',
    edad: null,
    bio: '',
    nivel: '',
    intereses: [],
    pais: null,
    tecnologias: []
  })

  const paises = [
    { code: 'CL', name: 'Chile' },
    { code: 'AR', name: 'Argentina' },
    { code: 'MX', name: 'México' }
  ]

  const tecnologias = ['Vue', 'React', 'Angular', 'Svelte']

  const formValido = computed(() =>
    form.nombre.trim() !== '' &&
    form.edad >= 0 && form.edad <= 120 &&
    form.intereses.length > 0
  )

  function enviar() {
    alert(JSON.stringify(form, null, 2))
  }
</script>

<template>
  <div class="formulario">
    <h2>Registro / Perfil</h2>

    <!-- Datos básicos -->
    <label>Nombre:
      <input type="text" v-model.trim="form.nombre" />
    </label>

    <label>Edad:
      <input type="number" v-model.number="form.edad" min="0" max="120" />
    </label>

    <label>Biografía:
      <textarea v-model.lazy="form.bio"></textarea>
      <p>Caracteres: {{ form.bio.length }}</p>
    </label>

    <!-- Preferencias -->
    <fieldset>
      <legend>Nivel</legend>
      <label><input type="radio" value="junior" v-model="form.nivel" /> Junior</label>
      <label><input type="radio" value="semi senior" v-model="form.nivel" /> Semi Senior</label>
      <label><input type="radio" value="senior" v-model="form.nivel" /> Senior</label>
    </fieldset>

    <fieldset>
      <legend>Intereses</legend>
      <label><input type="checkbox" value="Frontend" v-model="form.intereses" /> Frontend</label>
      <label><input type="checkbox" value="Backend" v-model="form.intereses" /> Backend</label>
      <label><input type="checkbox" value="DevOps" v-model="form.intereses" /> DevOps</label>
    </fieldset>

    <label>País:
      <select v-model="form.pais">
        <option v-for="p in paises" :key="p.code" :value="p">
          {{ p.name }}
        </option>
      </select>
    </label>

    <label>Tecnologías:
      <select v-model="form.tecnologias" multiple>
        <option v-for="t in tecnologias" :key="t" :value="t">
          {{ t }}
        </option>
      </select>
    </label>

    <!-- Vista previa -->
    <div class="preview">
      <h3>Resumen en tiempo real</h3>
      <p>Nombre: {{ form.nombre }}</p>
      <p>Edad: {{ form.edad }}</p>
      <p>Biografía: {{ form.bio }}</p>
      <p>Nivel: {{ form.nivel }}</p>
      <p>Intereses: {{ form.intereses.join(', ') }}</p>
      <p>País: {{ form.pais?.name }}</p>
      <p>Tecnologías: {{ form.tecnologias.join(', ') }}</p>
    </div>

    <!-- Botón de envío -->
    <button :disabled="!formValido" @click="enviar">Enviar</button>
  </div>
</template>



<style>
  body {
    font-family: Arial, sans-serif;
    background-color: #f0f2f5;
    padding: 20px;
  }

  .formulario {
    max-width: 420px;
    margin: auto;
    background: white;
    padding: 24px;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  }

  h2 {
    text-align: center;
    color: #333;
    margin-bottom: 20px;
  }

  label {
    display: block;
    margin-bottom: 12px;
    color: #555;
    font-size: 14px;
  }

  input[type="text"],
  input[type="number"],
  textarea,
  select {
    display: block;
    width: 100%;
    padding: 8px;
    margin-top: 4px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 14px;
    box-sizing: border-box;
  }

  textarea {
    resize: vertical;
    min-height: 80px;
  }

  fieldset {
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 10px 14px;
    margin-bottom: 12px;
  }

  legend {
    color: #555;
    font-size: 14px;
    padding: 0 4px;
  }

  fieldset label {
    display: inline-block;
    margin-right: 12px;
    margin-bottom: 0;
  }

  button {
    width: 100%;
    padding: 10px;
    margin-top: 16px;
    background-color: #42b883;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 15px;
    cursor: pointer;
  }

  button:disabled {
    background-color: #aaa;
    cursor: not-allowed;
  }

  .preview {
    margin-top: 20px;
    padding: 14px;
    background-color: #f9f9f9;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 14px;
    color: #444;
  }

  .preview h3 {
    margin-top: 0;
    color: #333;
  }

  .preview p {
    margin: 6px 0;
  }
</style>
