<template>
  <div
    class="display-letter"
    :class="{
      'display-letter-special': isSpecialChar,
      'display-letter-correct': end && visible,
      'display-letter-error': end && !visible,
    }"
  >
    {{ visible || end ? letter.toUpperCase() : "" }}
  </div>
</template>

<script>
export default {
  name: "DisplayLetterComponent",

  props: {
    letter: { type: String, required: true },
    visible: { type: Boolean, default: false },
    isSpecialChar: { type: Boolean, default: false },
    end: { type: Boolean, default: false },
  },

  methods: {
    isSpace() {
      return this.letter === " ";
    },
  },
};
</script>

<style lang="scss" scoped>
.display-letter {
  width: $displayLetterSize;
  max-width: $displayLetterSize;
  min-height: $displayLetterSize;
  align-items: center;
  align-content: center;
  padding: $displayLetterSize/4;
  font-size: $displayLetterSize;
  margin-right: 7px;
  color: $white;
  text-align: center;
  border-bottom: $displayLetterBorder solid $white;
  font-weight: bold;

  @include sm {
    width: $displayLetterSize/2;
    max-width: $displayLetterSize/2;
    min-height: $displayLetterSize/2;
    padding: $displayLetterSize/2 $displayLetterSize/3;
  }

  &:last-child {
    margin-right: 0;
  }

  &.display-letter-special {
    border-bottom: none;
  }

  &.display-letter-correct {
    color: $greenLight;
  }

  &.display-letter-error {
    color: $redLight;
  }
}
</style>
