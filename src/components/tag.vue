<template>
    <div class="tag">
        <p><slot></slot></p>
    </div>
</template>

<script setup>

</script>

<style scoped>
.tag {
  background: #64766a;
  color: white;

  padding: 2px 10px;
}

p {
    font-size: clamp(0.6rem, 1.5vh, 1.2rem);
}
</style>