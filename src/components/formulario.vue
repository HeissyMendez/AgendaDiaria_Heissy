<template>
    <div>
    <div class="row">
      <div class="col-md-12">
        <h3 class="text-center">Tareas</h3>
        <label for="">Titulo</label>
        <input type="text" class="form-control" v-model="titulo">
        <div class="form-text">
          Modificado por ultima vez 12-10-2021 por Heissy Hernandez
        </div>
      </div>
      <div class="col-md-4">
        <label class="text-center">Encargados</label>
        <select v-model="encargado" class="form-control">
          <option value="" disabled selected>Elige un encargado</option>
          <option
            v-for="(Dato, index) in Encargados"
            :key="index"
            :value="Dato.nombre"
          >
            {{ Dato.nombre }}&nbsp;{{ Dato.apellido }}
          </option>
        </select>
      </div>
      <div class="col-md-4">
        <label class="text-center">Depositos</label>
        <select v-model="depositos" class="form-control">
          <option value="" disabled selected>Elige un deposito</option>
          <option
            v-for="(Dato, index) in Deposito"
            :key="index"
            :value="Dato.id"
          >
            {{ Dato.descripcion }}
          </option>
        </select>
      </div>
      <div class="col-md-4">
        <label class="text-center">Progresos</label>
        <select  v-model="progreso" class="form-control">
          <option value="" disabled selected>Elige un progreso</option>
          <option
            v-for="(Dato, index) in Progresos"
            :key="index"
            :value="Dato.id"
          >
            {{ Dato.descripcion }}
          </option>
        </select>
      </div>
      <div class="col-md-4">
        <label class="text-center">Prioridades</label>
        <select  v-model="prioridad" class="form-control">
          <option value="" disabled selected>Elige una prioridad</option>
          <option
            v-for="(Dato, index) in Prioridades"
            :key="index"
            :value="Dato.descripcion"
          >
            {{ Dato.descripcion }}
          </option> 
        </select>
      </div>
      <div class="row">
        <div class="col-md-4">
          <label class="text-center">Fecha inicio</label>
          <input  v-model="fechainicio" type="date" class="form-control" />
        </div>
        <div class="col-md-4">
          <label class="text-center">Fecha de vencimiento</label>
          <input  v-model="fechavencimiento" type="date" class="form-control" />
        </div>
      </div>

      <div class="row col-md-12">
          <label class="text-center">Nota</label>
          <textarea  v-model="nota" cols="4" rows="2"></textarea>
        </div>

        <div class="col-md-12">
        <label>Lista de comprobacion</label>
        </div>
        
         <div class=" row justify-content-end">
           <div class="col-md-3">
        <button class="btn btn-warning mt-2" @click="Guardar" >Guardar</button>
      </div>
      </div>
      </div>
    </div>
</template>

<script>
export default {
  name: "Tarea",
  data() {
    return {
      Encargados: [
        {
          id: 1,
          nombre: "Heissy",
          apellido: "Hernandez",
        },
        {
          id: 2,
          nombre: "Jairo",
          apellido: "Gregorio",
        },
      ],
      Deposito: [
        { id: 1, descripcion: "Pendiente" },
        { id: 2, descripcion: "Validacion" },
        { id: 3, descripcion: "Iniciado" },
        { id: 4, descripcion: "Produccion" },
        { id: 5, descripcion: "Finalizados" },
      ],
      Progresos: [
        { id: 1, descripcion: "No iniciada" },
        { id: 2, descripcion: "En curso" },
        { id: 3, descripcion: "Completada" },
      ],
      Prioridades: [
        { id: 1, descripcion: "Baja" },
        { id: 2, descripcion: "Media" },
        { id: 3, descripcion: "Alta" },
        { id: 4, descripcion: "Urgente" },
      ],
      titulo: "",
      depositos: "",
      encargado: "",
      progreso: "",
      prioridad: "",
      fechainicio: "",
      fechavencimiento: "",
      nota: "",
      listadecomprabacion: [],
      FilasTabla : [] 
    }
  },
  methods : {
      Guardar(){
          this.FilasTabla.push(
              {
                  title: this.titulo,
                  manager: this.encargado,
                  priority: this.prioridad,
                  final_date : this.fechavencimiento,
                  note: this.nota

              }
          );
            this.$emit('filas', this.FilasTabla);

      }
    }
}
</script>