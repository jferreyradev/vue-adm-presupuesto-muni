<script setup></script>

<template>
  <div>
    <fieldset>
      <legend>Datos principales</legend>
      <label for="dcto">Decreto</label>
      <input type="text" name="dcto" id="dcto" />
      <label for="dte">Fecha</label>
      <input type="date" name="" id="" />
      <label for="dest">Destinatario</label>
      <input type="text" name="dest" id="dest" />
      <label for="concepto">Concepto</label>
      <input type="text" name="concepto" id="dest" />
    </fieldset>
    <div class="inputlay">
      <fieldset>
        <legend>Retencinoes</legend>
        <div class="inputbox">
          <label for="desc">Observaciones</label>
          <input type="text" name="desc" id="desc" />
          <label for="porc">Porcentaje</label>
          <input type="number" name="porc" id="porc" />
          <label for="importe">Importe</label>
          <input type="number" name="importe" id="importe" />
        </div>
        <label for="tot">Total</label>
      </fieldset>
      <div>
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
        <button>Ingresar</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
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
