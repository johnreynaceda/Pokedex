<template>
  <div class="relative">
    <div
      @mouseover="isOpen = true"
      @mouseleave="isOpen = false"
      :class="color"
      class="h-12 w-12 rounded-xl shadow-md flex items-center justify-center"
    >
      <slot />
    </div>
    <div
      v-show="isOpen"
      class="
        absolute
        ml-20
        p-2
        bg-white
        -top-2
        shadow-lg
        rounded-t-lg rounded-br-lg
      "
    >
      {{ title }}
    </div>
  </div>
</template>

<script>
export default {
  props: ['color', 'title'],
  data() {
    return {
      isOpen: false,
    }
  },
}
</script>
