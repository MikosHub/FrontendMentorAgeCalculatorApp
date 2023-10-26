<template>
  <div>
    <span>{{ value }}</span>
    <span>{{ text }}</span>
  </div>
</template>

<script>

export default {

  props: {
    value: String,
    text: String,
  },
  watch: {
    value(newValue, oldValue) {
      console.log(`new: ${newValue} old: ${oldValue}`);
    }
  }
}


</script>