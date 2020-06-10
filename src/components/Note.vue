<template>
  <div class="note" :class="{ full: !grid }">
    <div class="note-header" :class="{ full: !grid }">
      <p :class="textClassName">{{data.title}}</p>
      <p style="cursor: pointer;" @click="removeNote(index)">x</p>
    </div>
    <div class="note-body">
      <p>{{ data.descr }}</p>
      <span>{{ data.date }}</span>
      <div class="buttons">
        <button @click="changeClassElement('standart')">standard</button>
        <button @click="changeClassElement('middle')">middle</button>
        <button @click="changeClassElement('danger')">danger</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Object
    },
    grid: {
      type: Boolean,
      default: true,
      required: true
    },
    index: {
      type: Number
    }
  },
  data() {
    return {
      textClassName: "standart"
    };
  },
  methods: {
    removeNote(index) {
      this.$emit("remove", index);
    },
    changeClassElement(className) {
      this.textClassName = className;
    }
  }
};
</script>

<style>
</style>