<template>
  <div :class="textClasses">
    <slot />
  </div>
</template>
  
<script lang="ts">
import { defineProps, computed } from "vue";

export default {
  props: defineProps({
    tag: {
      type: String,
      default: "span",
      validator: (value) => ["span", "h1", "h2", "h3"].includes(value),
    },
    bold: {
      type: Boolean,
      default: false,
    },
    italic: {
      type: Boolean,
      default: false,
    }
  }),

  setup(props) {
    const textClasses = computed(() => {
      const classes = [props.tag];

      if (props.bold) {
        classes.push("font-bold");
      }
      if (props.italic) {
        classes.push("italic");
      }

      return classes.join(" ");
    });

    return {
      textClasses,
    };
  },
};
</script>
  
  <style scoped>
/* Add your global styles here */
</style>
  