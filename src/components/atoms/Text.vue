<template>
  <component :is="tag" :class="textClasses" class="text">
    <slot />
  </component>
</template>
  
  <script lang="ts">
import { computed } from "vue";

export default {
  props: {
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
    },
  },

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
.text {
  display: block;
  line-height: 1.5;
  color: #333;
}

.text h1 {
  font-size: 2rem;
  line-height: 2.5rem;
}

.text h2 {
  font-size: 1.5rem;
  line-height: 2rem;
}

.text h3 {
  font-size: 1.25rem;
  line-height: 1.75rem;
}

.text.font-bold {
  font-weight: bold;
}

.text.italic {
  font-style: italic;
}
</style>
  
