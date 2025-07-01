<template>
  <div class="card">
    <h3>What is Vue</h3>
    
    <div class="card-body">
      <slot name="left"></slot> 
      <slot name="right"></slot> 
    </div>

    <h3><p>Structure of Vue</p></h3>
  </div>
</template>

<script>
export default {
  name: 'CardWrapper'
};
</script>

<style scoped>
.card {
  border: 2px solid #ccc;
  padding: 10px;
  margin-bottom: 20px;
}
.card-body {
  display: flex;
  justify-content: space-between;
  gap: 20px;
}
</style>
