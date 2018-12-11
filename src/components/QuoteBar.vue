<template>
  <div class="progress" style="height: 50px;">
    <div
      class="progress-bar"
      role="progressbar"
      :style="{width: quoteProgress + '%'}"
      aria-valuemin="0"
      aria-valuemax="100"
    >
    <h4>
    {{quotes.length + '/10 Quotes'}}

    </h4>
    </div>
  </div>
</template>

<script>
export default {
  props: ["quotes"],
  computed: {
    quoteProgress() {
      return this.quotes.length * 10;
    }
  }
};
</script>

<style>
</style>
