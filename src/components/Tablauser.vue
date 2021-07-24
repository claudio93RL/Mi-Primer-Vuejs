<template>
  <div class="row container mx-auto">
    <table class="table mt-4">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Nombre</th>
          <th scope="col">Apellido</th>
          <th scope="col">Rut</th>
          <th scope="col">Fecha De Nacimiento</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(persona, index) in personas" :key="index">
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ persona.nombre }}</td>
          <td>{{ persona.apellido }}</td>
          <td>{{ persona.rut }}</td>
          <td>{{ persona.edad }}</td>
        </tr>
      </tbody>
    </table>
    <div class="col-12 mt-5">
      <button class="btn btn-primary" @click="borrarUltimo">
        Borrar el ultimo
      </button>
      <br />
      <input type="text" placeholder="Nombre" v-model="nuevaPersona.nombre" />
      <input
        type="text"
        placeholder="Apellido"
        v-model="nuevaPersona.apellido"
      />
      <input type="text" placeholder="RUN" v-model="nuevaPersona.rut" />
      <input
        type="text"
        placeholder="Fecha de Nacimiento"
        v-model="nuevaPersona.edad"
      />
      <button class="btn btn-secondary" @click="agregarPersona">
        Agregar persona
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Tablauser",
  data() {
    return {
      nuevaPersona: {
        nombre: "",
        apellido: "",
        rut: "",
        edad: "",
      },
      personas: [],
    };
  },
  methods: {
    agregarPersona() {
      // this.personas.push(JSON.parse(JSON.stringify(this.nuevaPersona)));
      this.personas.push({ ...this.nuevaPersona });
      this.nuevaPersona = {
        nombre: "",
        apellido: "",
        rut: "",
        edad: "",
      };
    },
    borrarUltimo() {
      this.personas.pop();
    },
  },
};
</script>