<template>
  <div>
    <h3 v-if="title">
      {{ title }}
    </h3>
    <input
      v-model="value"
      :placeholder="placeholder"
      :maxlength="maxLength"
      @input="$emit('change', value)"
    >
    <span :class="feedbackType">{{ feedbackMessage }}&nbsp;</span>
  </div>
</template>

<script>
export default {
  name: 'TextField',
  props: {
    title: String,
    placeholder: String,
    initialValue: String,
    maxLength: Number,
    feedbackType: String,
    feedbackMessage: String
  },
  data() {
    return {
      value: ''
    };
  },
  created() {
    this.value = this.initialValue;
  },
  methods: {
    input: function(value) {
      this.value = value;
      this.$emit('change', value);
    }
  }
};
</script>

<style scoped lang="scss">
h3 {
    font-weight: 700;
    font-size: 1.1em;
    margin: 15px 0 0;
    color: inherit;
}

input { // overwrite Chrome style styles
    display: block;
    width: 100%;
    margin: 8px 0 4px !important;
    padding: 8px 12px !important;
    font: inherit !important;
    font-size: 1.1em !important;
    border-radius: 3px !important;
    color: inherit !important;
    background: #fff;
    outline: none !important;
    transition: box-shadow .1s !important;

    &:focus{
        box-shadow: 0 0 0 4px #C8E0F0;
    }
}

span {
    font-size: .9em;
    margin: 0 0 20px;

    &.ok {
      color: #4F8A10;
    }

    &.warning {
      color: #9F6000;
    }

    &.error {
        color: #D8000C;
    }
}
</style>
