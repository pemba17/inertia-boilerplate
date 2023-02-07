<template>
  <li class="mb-1 last:mb-0">
    <Link
      class="block transition duration-150 truncate"
      :class="activeClass"
      :href="href"
    >
      <span
        class="text-sm font-medium lg:opacity-0 lg:sidebar-expanded:opacity-100 2xl:opacity-100 duration-200"
        >{{ label }}</span
      >
    </Link>
  </li>
</template>

<script setup>
import { Link, usePage } from "@inertiajs/vue3";
import { computed } from "vue";
const props = defineProps({
  href: {
    type: String,
    required: true,
  },
  label: {
    type: String,
    required: true,
  },
  componentName: {
    type: String,
    required: true,
  },
});
const component = computed(() => usePage().component);

const activeClass = computed(() => {
  return component.value === props.componentName
    ? "text-indigo-500"
    : "text-slate-400 hover:text-slate-200";
});
</script>

<style></style>
