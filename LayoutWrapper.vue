<template>
  <div class="layout">
    <header class="header">
      <slot name="header"></slot>
    </header>

    <div class="top">
      <slot name="top"></slot>
    </div>

    <div class="body">
      <aside class="sidebar left">
        <slot name="left"></slot>
      </aside>

      <main class="main">
        <slot>Main Content</slot>
      </main>

      <aside class="sidebar right">
        <slot name="right"></slot>
      </aside>
    </div>

    <footer class="footer">
      <slot name="footer"></slot>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'LayoutWrapper'
};
</script>

<style scoped>
.layout {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  font-family: sans-serif;
}

.header, .footer {
  background-color: rgb(0, 255, 221);
  color: #fff;
  padding: 15px;
}

.top {
  background-color: #eee;
  padding: 10px;
}

.body {
  display: flex;
  flex: 1;
}

.sidebar {
  width: 200px;
  background-color: #f7f7f7;
  padding: 10px;
}

.left {
  border-right: 1px solid #ccc;
}

.right {
  border-left: 1px solid #ccc;
}

.main  {
  flex: 1;
  padding: 20px;
  background-color: #fff;
}
</style>
