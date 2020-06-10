<template>
  <!-- note list -->
  <div class="notes">
    <Note
      v-for="(note, index) in notes"
      :key="index"
      :grid="grid"
      :data="note"
      :index="index"
      @remove="removeNote"
    />
  </div>
</template>

<script>
import Note from "@/components/Note";

export default {
  components: {
    Note
  },
  props: {
    notes: {
      type: Array,
      required: true
    },
    grid: {
      type: Boolean,
      required: true
    }
  },
  data: () => ({
    textClassName: "standart"
  }),
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

<style lang="scss">
.notes {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 40px 0;
}
.note {
  width: 48%;
  padding: 18px 20px;
  margin-bottom: 20px;
  background-color: #ffffff;
  transition: all 0.25s cubic-bezier(0.02, 0.01, 0.47, 1);
  box-shadow: 0 30px 30px rgba(0, 0, 0, 0.02);
  &:hover {
    box-shadow: 0 30px 30px rgba(0, 0, 0, 0.04);
    transform: translate(0, -6px);
    transition-delay: 0s !important;
  }
  &.full {
    width: 100%;
    text-align: center;
  }
}
.note-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  h1 {
    font-size: 32px;
  }
  p {
    font-size: 22px;
    color: #402caf;
    &.middle {
      background: #cbd83a;
      color: #fff;
    }
    &.danger {
      background: red;
      color: #000;
    }
  }
  svg {
    margin-right: 12px;
    color: #999999;
    &.active {
      color: #402caf;
    }
    &:last-child {
      margin-right: 0;
    }
  }
  &.full {
    justify-content: center;
    p {
      margin-right: 16px;
      &:last-child {
        margin-right: 0;
      }
    }
  }
}
.note-body {
  display: flex;
  flex-direction: column;

  p {
    margin: 20px 0;
  }
  span {
    font-size: 14px;
    color: #999999;
  }
}
.buttons {
  display: flex;
  justify-content: flex-end;
  button {
    cursor: pointer;
    font-size: 14px;
    border-radius: 15px;
    margin-right: 5px;
    &:last-child {
      margin-right: 0;
    }
  }
}
</style>

