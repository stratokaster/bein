<template>
  <div>
    <h1 class="page__title">{{ $route.name }}</h1>
    <mainLayouts></mainLayouts>
  </div>
</template>
<script>
export default {
  layout: "lClient",
  name: "Components",
};
</script>
