<script setup>
import AppModal from '../components/AppModal.vue'
import { ref } from 'vue'
import data from '../assets/presup.json'

const showInnerForm = ref(false)
const selected = ref('')
</script>

<template>
  <div>
    <fieldset class="border-solid border-black border-2 p-4">
      <legend>Datos principales</legend>
      <div class="flex">
        <div class="flex flex-col p-1">
          <div>
            <label for="dcto">Decreto</label>
            <input type="text" name="dcto" id="dcto" placeholder="dcto" />
            <label for="dte">Fecha</label>
            <input type="date" name="" id="" />
          </div>
          <label for="dest">Destinatario</label>
          <input type="text" name="dest" id="dest" />
          <label for="concepto">Concepto</label>
          <input type="text" name="concepto" id="dest" />
        </div>
      </div>
    </fieldset>
    <div class="flex">
      <fieldset class="border-solid border-black border-2 p-4">
        <legend>Retenciones</legend>
        <div class="form-input-wrapper">
          <label for="desc">Observaciones</label>
          <input type="text" name="desc" id="desc" />
          <label for="porc">Porcentaje</label>
          <input type="number" name="porc" id="porc" />
          <label for="importe">Importe</label>
          <input type="number" name="importe" id="importe" />
        </div>
        <label for="tot">Total</label>
      </fieldset>

      <fieldset class="border-solid border-black border-2 p-4">
        <legend>Cargas</legend>
        <table>
          <tr>
            <th>Descripcion</th>
            <th>Importe</th>
          </tr>
          <tr>
            <td>Importe a descontar en concepto de utileria</td>
            <td>10000</td>
          </tr>
        </table>
        <button class="button" @click="showInnerForm = true">Ingresar</button>
      </fieldset>
    </div>
  </div>
  <AppModal :show="showInnerForm" title="Carga preliminar" @close="showInnerForm = false">
    
      <div>
        <div class="p-2 m-2">
          <input type="text" name="search" id="search" placeholder="Busqueda" />
        </div>
        <div class="max-h-72 overflow-auto text-black">
          <select size="5" v-model="selected">
            <option v-for="item in data" :key="item.IDDETPRE" :disabled = "item.HIJO==0?true:false" >
              {{ item.CUENTA }} - {{ item.DESCRIPCION }}
            </option>
          </select>
        </div>
      </div>
    <span>Tabla de cargas con importe preliminar</span>
  </AppModal>
</template>

<style scoped>
input {
  @apply form-input;
}
.boxform {
  border: solid 1px gainsboro;
  border-radius: 1rem;
  padding: 1rem;
}
.inputbox {
  display: flex;
  flex-direction: column;
}
.inputlay {
  display: flex;
}
</style>
