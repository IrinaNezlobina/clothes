<template>
  <div class="container">
    <div class="grid grid-cols-2 gap-3 pt-5">
      <RightComponent/>
      <LeftComponent/>
    </div>
  </div>
</template>
<script>
import { defineComponent, defineAsyncComponent } from 'vue';

export default defineComponent({
  components: {
    LeftComponent: defineAsyncComponent(() => import('./components/RightComponent.vue')),
    RightComponent: defineAsyncComponent(() => import('./components/LeftComponent.vue')),
  },
});
</script>
