<script>
  export default {
    props: [
      'active'
    ]
  }
</script>

<template>
  <button :disabled="!active">
    <svg
      id="random" :style="`filter: brightness(${active ? 1 : 0.5})`"
      xmlns="http://www.w3.org/2000/svg"
      width="50"
      height="50"
      fill="var(--color-heading)"
      viewBox="0 0 32 32"
    >
      <path d="M0 24q0 .832.576 1.44t1.44.576H4q2.048 0 3.904-.8t3.168-2.144 2.144-3.2.8-3.872q0-2.464 1.728-4.224T20 10.016h4V12q0 .672.384 1.152t.864.704 1.12.128 1.056-.544l4-4Q32.032 8.8 32 8t-.576-1.408l-4-4q-.48-.448-1.088-.544t-1.12.128-.864.704T24 4v2.016h-4q-2.016 0-3.872.8t-3.2 2.112-2.144 3.2T10.016 16q0 2.496-1.76 4.256T4 22.016H2.016q-.832 0-1.44.576T0 24M0 8.032q0 .832.576 1.408t1.44.576H4q1.408 0 2.592.608t2.08 1.664q.672-2.048 1.984-3.68Q7.744 6.016 4 6.016H2.016q-.832 0-1.44.608T0 8.032m13.376 15.424q2.848 2.56 6.624 2.56h4v2.016q0 .64.384 1.152t.864.704 1.12.096 1.056-.544l4-4q.608-.608.576-1.44t-.576-1.376l-4-4q-.48-.48-1.088-.576t-1.12.128-.864.736-.352 1.12v1.984h-4q-1.376 0-2.592-.576t-2.048-1.664q-.704 2.048-1.984 3.68"></path>
    </svg>
  </button>
</template>

<style scoped>
button {
  background-color: transparent;
  padding: 15px;
  aspect-ratio: 1;
  object-fit: cover;
  border: 2px solid var(--color-text);
  border-radius: 30px;
  margin: 0 10px;
}
#random {
  width: 50px;
  position: relative;
}
</style>
