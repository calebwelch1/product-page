
<template>
  <main>
    <div
    class="flex-row"
    style="border: 1px solid white;"
    >
    <p>1</p>
    <p>2</p>
  </div>
  </main>
</template>
<script>

export default {
  data() {
    return {
      items: [],
    };
  },
}
</script>

<style>
body{
  margin:0 !important;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: slate-grey;
  background-color: transparent;
}
.hi{
  color:black;
}

.flex-row {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

@media (max-width: 900px) {
  .flex-row {
    display: flex;
  flex-direction: column;
  justify-content: space-between;
  }
}
</style>
