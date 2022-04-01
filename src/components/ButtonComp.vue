<template>
  <button
    :style="{ background: color }"
    class="btn"
    @click="$emit('btn-click')"
  >
    {{ text }}
  </button>
</template>
<script>
export default {
  name: "ButtonComp",
  props: {
    text: String,
    color: String,
  },
};
</script>
