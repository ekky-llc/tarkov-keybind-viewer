<script setup>
defineProps(['keybinds']);

function camelCaseToWords(s) {
  const result = s.replace(/([A-Z])/g, ' $1');
  return result.charAt(0).toUpperCase() + result.slice(1);
}
// console.log(props.keybinds)
</script>

<template>
  <table>
    <thead>
      <tr>
        <th>Action</th>
        <th>Key</th>
        <th>Key</th>
        <th>Press Type</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="keybind in keybinds.keyBindings" :key="keybind.keyName">
        <td>{{ camelCaseToWords(keybind.keyName) }}</td>
        <td :class="`${keybind.variants[0].keyCode.length || 'not_set'}`">{{ camelCaseToWords(keybind.variants[0].keyCode.join(' + ')).replace('Alpha', '') || 'Not Set' }}</td>
        <td :class="`${keybind.variants[1].keyCode.length || 'not_set'}`">{{ camelCaseToWords(keybind.variants[1].keyCode.join(' + ')).replace('Alpha', '') || 'Not Set' }}</td>
        <td>{{ camelCaseToWords(keybind.pressType) }}</td>
      </tr>
    </tbody>
  </table>
</template>XX

<style scoped>
  table {
    background: #091416;
    padding: 8px;
    color: #f1e8c0;
  }

  thead th {
    text-align: left;
  }

td:nth-of-type(1) {
  width: 300px;
}

  td:nth-of-type(2),
  td:nth-of-type(3) {
    width: 250px;
  }

  td:nth-of-type(4) {
    width: 200px;
  }

  td, th {
    background: #202020;
    padding: 4px;
  }

  .not_set {
    opacity: 0.25;
  }
</style>
