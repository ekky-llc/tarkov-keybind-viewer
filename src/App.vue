<script setup>
import { ref } from 'vue'
import KeyBinds from './components/KeyBinds.vue'
import keybind_json from './data.json'

const modal_state = ref(false);
const modal_upload = ref('');
const keybind_data = ref(keybind_json);

</script>

<template>
  <div class="main">
    <div v-if="modal_state" class="modal">
      <div class="modal_container">
        <div class="instructions">
          <strong>G'day, whipped this up in like 15 minutes for people to view Tarkov Keybind files. </strong><br/><br/>
          Open File Explorer, type in `%appdata%`<br/>
          Go back one folder, then go to Roaming <br/>
          Open Battlestate Games, then EFT, then Settings<br/><br/>
          Copy the contents of the Control.ini file into the below textbox.<br/><br/>
          <strong>Cya on Customs</strong>
        </div>
        <textarea v-model="modal_upload"></textarea>
        <div class="button_group">
          <button @click="() =>{ modal_state = false}">Close</button>
          <button @click="() =>{ keybind_data = JSON.parse(modal_upload); modal_state = false}">Save</button>
        </div>
      </div>
    </div>
    <button @click="() => modal_state = true">Upload Config File</button>
    <KeyBinds :keybinds="keybind_data" />
  </div>
</template>

<style scoped>

  .instructions {
    color: #f1e8c0;
    margin-bottom: 8px;
    max-width: 100%;
    font-size: 12px;
  }
  .main {
    position: relative;
    display: flex;
    flex-direction: column;
    gap: 16px;
    justify-content: center;
    max-width: 980px;
    margin: 0 auto;
  }

  .modal {
    position: fixed;
    height: 100vh;
    width: 100vw;
    top:0;
    left: -25px;
    background: rgba(0,0,0,0.75);
    display: grid;
    place-content: center;
    z-index: 999;
  }

  .modal_container {
    display: flex;
    flex-direction: column;
    background: black;
    border: 1px solid #f1e8c0a1;
    border-radius: 3px;
    padding: 12px;
    height: fit-content;
  }

  .modal_container textarea {
    height: 500px;
    width: 500px;
    margin-bottom: 8px;
  }

  .button_group {
    display: flex;
    justify-content: space-between;
  }

  button {
    padding: 8px 16px;
    background: none;
    color: #f1e8c0;
    border: 1px solid #f1e8c0;
    outline: #f1e8c0;
  }

  button:hover {
    cursor: pointer;
    background: black;
  }
</style>
