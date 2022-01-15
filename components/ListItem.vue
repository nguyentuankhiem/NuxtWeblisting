<template>
    <div
      class="md:grid md:grid-cols-2 hover:bg-gray-50 md:space-y-0 space-y-1 p-4 border-b"
    >
      <p class="text-gray-600">{{itemKey}}</p>
      <p>{{ itemValue }}</p>
    </div>
</template>

<script>
export default {
  props: {
    itemKey: String,
    itemValue: String
  }
};
</script>

<style></style>
