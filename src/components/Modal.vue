<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-body" @click="$emit('start')">
            <slot></slot>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.modal-mask {
  position: absolute;
  z-index: 9998;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  width: 100%;
  min-height: 100%;
  border-radius: 10px;
  background-color: rgba(0, 0, 0, .2);
  transition: opacity .3s ease;
}

.modal-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  z-index: 9998;
}

.modal-container {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: all .3s ease;
}

.modal-body {
    background-color: #000;
    color: #fff;
    cursor: pointer;
    padding: 50px;
}


</style>
