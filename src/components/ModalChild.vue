<script setup>
defineProps({
  show: Boolean
})
</script>
<template>
  <Transition name="modal">
    <div v-if="show" class="modal-mask">
      <div class="modal-container">
        <div class="modal-header">
          <slot name="header">Sample modal</slot>
        </div>
        <div class="modal-body">
          <slot name="body">Body of modal dialog</slot>
        </div>
        <div class="modal-footer">
          <slot name="footer">
            Modal footer
            <button
              class="modal-default-button2"
              @click="$emit('close')"
            >OK</button>
            <button
              class="modal-default-button2"
              @click="$emit('close')"
            >Cancel</button>

          </slot>
        </div>
      </div>
    </div>
  </Transition>
</template>
<style>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  transition: opacity 0.3s ease;
}
.modal-container {
  min-width: 300px;
  margin: auto;
  padding: 20px 30px;
  background-color:#181818;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  border-radius: 15px;
}
.modal-header h3 {
  margin-top: 0;
  color: #69CCC9;
}
.modal-body {
  margin: 20px 0;
}
.modal-default-button {
  float: right;
}
.modal-default-button2 {
  float: right;
  background-color: black;
}
.modal-enter-from {
  opacity: 0;
}
.modal-leave-to {
  opacity: 0;
}
.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
button {
  background-color: #181818;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
</style>