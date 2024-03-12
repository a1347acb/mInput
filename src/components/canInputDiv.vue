<script setup lang="ts">
import {defineProps, CSSProperties} from 'vue';

interface CanInputDivProps {
  placeholder?: string
  placeholderStyle?: CSSProperties
}
withDefaults(defineProps<CanInputDivProps>(), {
  placeholder: '测试文字内容123',
  placeholderStyle: {
    color: '#999',
    fontSize: '1em'
  }
})
</script>

<template>
  <div class="can-input-div" :style="$attrs.style" :class="$attrs.class">
    <span class="placeholder" :style="placeholderStyle">{{ placeholder }}</span>
    <div contenteditable="true" class="input-div">
      <span style="background: #f00;" contenteditable="false">测试文字</span>
    </div>
  </div>
</template>

<style scoped>
.can-input-div{
  font-size: 20px;
  background-color: #efefef;
  position: relative;
  padding: 10px;
}
.can-input-div > *{
  font-size: 1em;
  position: relative;
  z-index: 1;
}
.input-div{
  caret-color: #00f;
  outline: none;
}
.placeholder{
  position: absolute;
  z-index: 0;
  width: 100%;
  pointer-events: none;
}
</style>