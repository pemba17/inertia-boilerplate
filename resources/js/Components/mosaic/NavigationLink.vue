<template>
  <li
    class="px-3 py-2 rounded-sm mb-0.5 last:mb-0"
    :class="{
      'bg-slate-900': activeClass,
    }"
  >
    <Link
      class="block text-slate-200 hover:text-white truncate transition duration-150"
      :href="href"
      ><div class="flex items-center">
        <navigation-icon :icon="componentName" :active="activeClass" />
        <span
          class="text-sm font-medium ml-3 lg:opacity-0 lg:sidebar-expanded:opacity-100 2xl:opacity-100 duration-200"
          >{{ label }}</span
        >
      </div>
    </Link>
  </li>
</template>

<script setup>
import { Link, usePage } from "@inertiajs/vue3";
import { computed } from "vue";
import NavigationIcon from "@/Components/mosaic/NavigationIcon.vue";
const component = computed(() => usePage().component);
const props = defineProps({
  componentName: {
    type: String,
    required: true,
  },
  href: {
    type: String,
    required: true,
  },
  label: {
    type: String,
    required: true,
  },
});

const activeClass = computed(() => {
  if (component.value === props.componentName) return true;
  else return false;
});
</script>

<style></style>
