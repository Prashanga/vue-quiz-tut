<template>
  <div>
    <b-nav tabs>
      <b-nav-item disabled>
        <b>Fancy Quiz Application</b>
      </b-nav-item>
      <b-nav-item disabled>Counter: {{ correct }}/{{ total }}</b-nav-item>
    </b-nav>
  </div>
</template>

<script>
export default {
  props: {
    total: Number,
    correct: Number
  }
};
</script>

<style></style>
