<template>
  <div>
    <svg width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
    <g clip-path="url(#clip0_110_2)">
    <rect width="32" height="32" fill="white"/>
    <path fill-rule="evenodd" clip-rule="evenodd" d="M29.5 24.5915C26.6593 29.0458 21.6747 32 16 32C10.3253 32 5.34068 29.0458 2.5 24.5915H29.5ZM27.9539 23L19.5 14.2976L16 16L12.5 14.2976L4.04609 23H27.9539Z" fill="#D9D9D9"/>
    <path fill-rule="evenodd" clip-rule="evenodd" d="M16 0C21.2794 0 25.9616 2.55695 28.8757 6.5C29.0984 6.80131 29.3107 7.11071 29.5122 7.42769L2.48776 7.42769C5.32635 2.96266 10.3172 0 16 0ZM5.72033 9L16 14L26.2797 9H5.72033Z" fill="#D9D9D9"/>
    <path fill-rule="evenodd" clip-rule="evenodd" d="M0 16C0 13.4897 0.578113 11.1144 1.60847 9V23C0.578113 20.8856 0 18.5103 0 16ZM2.49823 22.1064L11 13.568L2.48919 9.42838L2.49823 22.1064Z" fill="#D9D9D9"/>
    <path fill-rule="evenodd" clip-rule="evenodd" d="M30.3915 9C31.4219 11.1144 32 13.4897 32 16C32 18.5103 31.4219 20.8856 30.3915 23V9ZM29.5108 9.42838L21 13.568L29.5018 22.1064L29.5108 9.42838Z" fill="#D9D9D9"/>
    </g>
    <defs>
    <clipPath id="clip0_110_2">
    <rect width="32" height="32" fill="white"/>
    </clipPath>
    </defs>
    </svg>
  </div>
</template>

<style>
svg {
  width: 32px;
  height: 32px;
}

#under {
  fill: var(--color-heading);
  position: absolute;
}

#over {
  fill: var(--color-text);
  z-index: 1;
  animation: unpress 200ms ease-in-out forwards;
}

#over:hover {
  animation: press 200ms ease-in-out forwards;
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
