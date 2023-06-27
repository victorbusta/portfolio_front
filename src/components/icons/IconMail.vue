<template>
  <a class="iconlink" href="mailto:victor.sdbustamante@gmail.com?subject=Prise de contact" target="_blank">
    <svg  viewBox="0 0 32 32"  xmlns="http://www.w3.org/2000/svg">
    <path fill-rule="evenodd" clip-rule="evenodd" d="M32 16C32 24.8366 24.8366 32 16 32C7.16344 32 0 24.8366 0 16C0 7.16344 7.16344 0 16 0C24.8366 0 32 7.16344 32 16ZM25.3571 6H6.69047C5.21772 6 4.02381 7.27919 4.02381 8.85714V23.1429C4.02381 24.7208 5.21772 26 6.69047 26H25.3571C26.8299 26 28.0238 24.7208 28.0238 23.1429V8.85714C28.0238 7.27919 26.8299 6 25.3571 6Z" />
    <path d="M23 23C24.1046 23 25 22.1046 25 21V16V11L16 16L7 11V16V21C7 22.1046 7.89543 23 9 23H16H23Z" />
    <path d="M16 9H9C8.93768 9 8.87603 9.00285 8.81517 9.00843L16 13L23.1848 9.00843C23.124 9.00285 23.0623 9 23 9H16Z" />
    </svg>


    <svg  viewBox="0 0 32 32"  xmlns="http://www.w3.org/2000/svg">
    <path fill-rule="evenodd" clip-rule="evenodd" d="M32 16C32 24.8366 24.8366 32 16 32C7.16344 32 0 24.8366 0 16C0 7.16344 7.16344 0 16 0C24.8366 0 32 7.16344 32 16ZM25.3571 6H6.69047C5.21772 6 4.02381 7.27919 4.02381 8.85714V23.1429C4.02381 24.7208 5.21772 26 6.69047 26H25.3571C26.8299 26 28.0238 24.7208 28.0238 23.1429V8.85714C28.0238 7.27919 26.8299 6 25.3571 6Z" />
    <path d="M23 23C24.1046 23 25 22.1046 25 21V16V11L16 16L7 11V16V21C7 22.1046 7.89543 23 9 23H16H23Z" />
    <path d="M16 9H9C8.93768 9 8.87603 9.00285 8.81517 9.00843L16 13L23.1848 9.00843C23.124 9.00285 23.0623 9 23 9H16Z" />
    </svg>

  </a>
</template>

<style scoped>
svg {
  position: relative;
  fill: var(--color-background-bis);
  width: 32px;
  height: 32px;
}

svg:first-child {
  position: absolute;
}

svg:last-child {
  fill: var(--color-text);
}

svg:last-child:hover {
  transform: translate(4px, -4px);
}
</style>