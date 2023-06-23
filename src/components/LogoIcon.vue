<template>

<div class="wrap">
  <div>
    <span class="head">
      <h1>V</h1><h1>i</h1><h1>c</h1><h1>t</h1><h1>o</h1><h1>r</h1><h1>&nbsp;</h1><h1>S</h1><h1>a</h1><h1>n</h1><h1>t</h1><h1>o</h1><h1>s</h1>
    </span>
    <span class="over first">
      <h1>V</h1><h1>i</h1><h1>c</h1><h1>t</h1><h1>o</h1><h1>r</h1><h1>&nbsp;</h1><h1>S</h1><h1>a</h1><h1>n</h1><h1>t</h1><h1>o</h1><h1>s</h1>
    </span>
  </div>

  <div>
    <span class="head">
      <h1>C</h1><h1>o</h1><h1>n</h1><h1>s</h1><h1>u</h1><h1>l</h1><h1>t</h1><h1>i</h1><h1>n</h1><h1>g</h1>
    </span>
    <span class="over second">
      <h1>C</h1><h1>o</h1><h1>n</h1><h1>s</h1><h1>u</h1><h1>l</h1><h1>t</h1><h1>i</h1><h1>n</h1><h1>g</h1>
    </span>
  </div>
</div>

</template>

<style lang="scss" scoped>
h1 {
  width: fit-content;
  font-weight: bold;
  font-size: 8vw;

  text-transform: uppercase;
}

div.wrap {
  position: relative;
  display: flex;
  flex-direction: column;
  width: fit-content;
}

span {
  display: flex;
  color: var(--color-heading);
}

span.head {
  position: absolute;
}

span.over > h1 {
  color: var(--color-text);
  z-index: 1;
  transition: all 200ms ease-in-out;
}

span.over > h1:hover {
  transform: translate(.7vw, -.7vw);
  filter: drop-shadow(.7vw .7vw .7vw rgba(0, 0, 0, 0.5));
}

@for $i from 1 through 13 {
  span.first > h1:nth-child(n + #{$i}) {
    animation: press-reverse 200ms ease-in-out calc(200ms + #{$i}00ms);
  }
}

@keyframes press-reverse {
  0% {
    transform: translate(0);
    filter: drop-shadow(0px 0px 0px rgba(0, 0, 0, 0.5));
  }
  30% {
    transform: translate(.7vw, -.7vw);
    filter: drop-shadow(.7vw .7vw .7vw rgba(0, 0, 0, 0.5));
  }
  100% {
    transform: translate(0);
    filter: drop-shadow(0px 0px 0px rgba(0, 0, 0, 0.5));
  }
}
</style>