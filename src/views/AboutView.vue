<template>
  <main>
    <span id="title">
      <h1>About</h1>
    </span>

  </main>
</template>

<style scoped>
main {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

#title > h1 {
  font-size: 8vw;
  font-weight: bolder;
  line-height: 8vw;
  color: var(--color-heading);
  margin-left: 16px;
  width: fit-content;
}
</style>
