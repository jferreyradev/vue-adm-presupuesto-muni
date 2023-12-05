<script setup>
import AppModal from '../components/AppModal.vue'
import { ref, computed } from 'vue'
import data from '../assets/presup.json'

const showInnerForm = ref(false)
const selected = ref('')
const selectedItems = ref([])

const total = computed(() =>
  selectedItems.value.reduce(
    (accumulator, currentValue) => accumulator + Number(currentValue.importe),
    0
  )
)

const handleSelect = (item) => {
  if (item['HIJO'] === 1) {
    let importe
    do {
      importe = 0
      importe = prompt('Ingrese el importe (9999.99)', importe)
    } while (isNaN(importe))
    //importe = Number(importe).toFixed(2)  id: Date.now(),
    selectedItems.value.push({
      item,
      importe: importe
    })
  }
}
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
          <option
            v-for="item in data"
            :key="item.IDDETPRE"
            :disabled="item.HIJO == 0 ? true : false"
            @dblclick="handleSelect(item)"
            @keyup.enter="handleSelect(item)"
          >
            {{ item.CUENTA }} - {{ item.DESCRIPCION }}
          </option>
        </select>
      </div>
    </div>
    <span>Tabla de cargas con importe preliminar</span>
    <table v-if="selected.length>0" >
      <thead>
        <tr class="bg-blue-400">
          <th class="border text-left px-2 py-1">Cuenta</th>
          <th class=" border text-left px-2 py-1">Descripción</th>
          <th class=" border text-left px-2 py-1">Importe</th>
          <th class=" border text-left px-2 py-1">Acción</th>
        </tr>
      </thead>
      <tbody>
        <tr class="hover:bg-blue-400" v-for="el in selectedItems" :key="el.item.IDDETPRE">
          <td>{{ el.item.CUENTA }}</td>
          <td>{{ el.item.DESCRIPCION }}</td>
          <td class="text-right">{{ el.importe }}</td>  
          <td>  </td>        
        </tr>
      </tbody>
      <tfoot>
        <tr class="bg-blue-400">
          <td class="border text-right py-1"></td>
          <td class="border text-right py-1">Total</td>
          <td class="border text-right py-1">{{ total }}</td>
          <td class="border text-right py-1"></td>
        </tr>
      </tfoot>
    </table>
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
