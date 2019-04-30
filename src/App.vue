<template>
  <div id="app">
    <h1>Beautiful Pokemon Battle Simulator</h1>
    <div id="fast-attack">
      <h3>Fast attack</h3>
      <label :for="fastDamage">Damage</label>
      <input type="number" :name="fastDamage" :id="fastDamage" v-model="fastDamageValue">

      <label :for="fastCooldown">Cooldown</label>
      <input type="number" :name="fastCooldown" :id="fastCooldown" v-model="fastCooldownValue">

      <label :for="fastEnergy">Energy</label>
      <input type="number" :name="fastEnergy" :id="fastEnergy" v-model="fastEnergyValue">
    </div>

    <div id="charged-attack">
      <h3>Charged attack</h3>
      <label :for="chargedDamage">Damage</label>
      <input type="number" :name="chargedDamage" :id="chargedDamage" v-model="chargedDamageValue">

      <label :for="chargedCooldown">Cooldown</label>
      <input
        type="number"
        :name="chargedCooldown"
        :id="chargedCooldown"
        v-model="chargedCooldownValue"
      >

      <label :for="chargedAmount">Charge amount</label>
      <select :id="chargedAmount" v-model="chargedAmountValue">
        <option value="3">Third</option>
        <option value="2">Half</option>
        <option value="1">Full</option>
      </select>
    </div>

    <div>
      <h3>Simulation</h3>
      <ul>
        <!-- Total Damage: c-damage + ((c-amount * 100) / f-energy) * f-damage -->
        <li>Total damage per charged attack: {{ chargedDamageValue + Math.ceil(1/parseInt(chargedAmountValue)*10)*10 / fastEnergyValue*fastDamageValue }}</li>
        <!-- Total Time: c-cooldown + ((c-amount * 100) / f-energy) * f-cooldown -->
        <li>Time elapsed per charged attack: {{ Math.ceil(1/parseInt(chargedAmountValue)*10)*10 / fastEnergyValue*fastCooldownValue + chargedCooldownValue }}</li>
        <li>Number of fast attacks per charged attack: {{ parseInt(Math.ceil(1/parseInt(chargedAmountValue)*10)*10) / fastEnergyValue }}</li>
        <li>
          <strong>Debug</strong>
        </li>
        <li>fast damage: {{ fastDamageValue }}</li>
        <li>fast cooldown: {{ fastCooldownValue }}</li>
        <li>fast energy: {{ fastEnergyValue }}</li>
        <li>charged damage: {{ chargedDamageValue }}</li>
        <li>charged cooldown: {{ chargedCooldownValue }}</li>
        <li>charged amount: {{ '1/' + chargedAmountValue }}</li>

        <li>(1/parseInt(chargedAmountValue)): {{ parseInt(1/parseInt(chargedAmountValue)) }}</li>
        <li>parseInt((1/parseInt(chargedAmountValue))*100/fastEnergyValue): {{ parseInt((1/parseInt(chargedAmountValue))*100/fastEnergyValue) }}</li>
        <li>parseInt((1/parseInt(chargedAmountValue))*100/fastEnergyValue)*fastDamageValue: {{ parseInt((1/parseInt(chargedAmountValue))*100/fastEnergyValue)*fastDamageValue }}</li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'app',
  components: {},
  data() {
    return {
      fastDamage: 'fast-attack-damage',
      fastCooldown: 'fast-attack-cooldown',
      fastEnergy: 'fast-attack-energy',
      chargedDamage: 'charged-attack-damage',
      chargedCooldown: 'charged-attack-cooldown',
      chargedAmount: 'charge-amount',
      fastDamageValue: 10,
      fastCooldownValue: 1,
      fastEnergyValue: 10,
      chargedDamageValue: 20,
      chargedCooldownValue: 2,
      chargedAmountValue: '3'
    }
  }
})
</script>


<style>
label {
  margin-right: 5px;
}

input {
  margin-right: 20px;
}

ul {
  list-style: none;
}

#fast-attack {
  margin-bottom: 50px;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>