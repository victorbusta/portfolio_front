<template>
  <div>
    <svg id="under" width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M28.4471 5.94578C25.5139 2.31902 21.0278 0 16 0C10.9722 0 6.48612 2.31902 3.55292 5.94578H4.5L27.5 5.94578H28.4471Z" />
    <path d="M19.5 14.2976L16 16L12.5 14.2976L5.01754 22H26.9825L19.5 14.2976Z" />
    <path d="M27.6181 10.349L23 12.5952L22 13.0816L27.8497 18.9852L27.6181 10.349Z" />
    <path d="M32 16C32 13.4897 31.4219 11.1144 30.3915 9L30.837 22C31.587 20.1471 32 18.1218 32 16Z" />
    <path d="M10 13.0816L4.38192 10.349L4.15034 18.9852L10 13.0816Z" />
    <path d="M1.60847 9C0.578113 11.1144 0 13.4897 0 16C0 18.1218 0.413014 20.1471 1.16303 22L1.60847 9Z" />
    <path d="M16 32C21.6747 32 26.6593 29.0458 29.5 24.5915H28H4H2.5C5.34068 29.0458 10.3253 32 16 32Z" />
    </svg>

    <svg id="over" width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M28.4471 5.94578C25.5139 2.31902 21.0278 0 16 0C10.9722 0 6.48612 2.31902 3.55292 5.94578H4.5L27.5 5.94578H28.4471Z" />
    <path d="M19.5 14.2976L16 16L12.5 14.2976L5.01754 22H26.9825L19.5 14.2976Z" />
    <path d="M27.6181 10.349L23 12.5952L22 13.0816L27.8497 18.9852L27.6181 10.349Z" />
    <path d="M32 16C32 13.4897 31.4219 11.1144 30.3915 9L30.837 22C31.587 20.1471 32 18.1218 32 16Z" />
    <path d="M10 13.0816L4.38192 10.349L4.15034 18.9852L10 13.0816Z" />
    <path d="M1.60847 9C0.578113 11.1144 0 13.4897 0 16C0 18.1218 0.413014 20.1471 1.16303 22L1.60847 9Z" />
    <path d="M16 32C21.6747 32 26.6593 29.0458 29.5 24.5915H28H4H2.5C5.34068 29.0458 10.3253 32 16 32Z" />
    </svg>
  </div>
</template>

<style scoped>
svg {
  width: 32px;
  height: 32px;
}

.back {
  /* fill: var(--color-background); */
  fill: none;
}

#under {
  fill: var(--color-heading);
  position: absolute;
}

#over {
  fill: var(--color-text);
  z-index: 1;
  animation: press 200ms ease-in-out forwards;
}

#over:hover {
  animation: unpress 200ms ease-in-out forwards;
}

@keyframes unpress {
  100% {
    transform: translate(2px, -2px);
    filter: drop-shadow(2px 2px 2px rgba(0, 0, 0, 0.2));
  }
}

@keyframes press {
  0% {
    transform: translate(2px, -2px);
    filter: drop-shadow(2px 2px 2px rgba(0, 0, 0, 0.2));
  }

  100% {
    transform: translate(0);
  }
}</style>
