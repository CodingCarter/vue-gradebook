<template>
  <form @submit="addgradeFormSubmit">
    <h3>Add new grade</h3>
    <label>
      Name
      <input
        type="text"
        placeholder="Verbs Practice"
        required
        v-model="formGrade.name"
      />
    </label>
    <label>
      <input
        type="number"
        placeholder="8"
        required
        v-model="formGrade.grade"
      />
      points out of
      <input
        type="number"
        placeholder="10"
        required
        v-model="formGrade.maxPoints"
      />
    </label>
    <div>
      <input type="submit" value="Add grade" />
    </div>
  </form>
</template>

<script lang="ts">
import type { GradeData } from "../models";

export default {
  props: ["addGrade"],
  data() {
    return {
      formGrade: {},
    }
  },
  methods: {
    addgradeFormSubmit(e: Event) {
      e.preventDefault();
      const self: any = this;
      self.addGrade({ ...self.formGrade } as GradeData);
      self.formGrade = {};
    },
  },
};
</script>

<style lang="scss" scoped>
form {
  display: flex;
  flex-direction: column;
  margin-top: 2rem;

  h3 {
    font-size: 2.3rem;
    margin: 0;
    margin-bottom: 0.4rem;
  }

  input {
    font-family: inherit;
  }

  label {
    margin: 0.65rem 0;

    input {
      margin: 0 0.4rem;
      padding: 0.25rem 0.5rem;
    }

    &:nth-of-type(2) {
      input:nth-of-type(1) {
        margin-left: 0;
      }
    }
  }

  div {
    margin-top: 1rem;

    input[type="submit"] {
      font-size: 1.1rem;
      padding: 0.5rem 1rem;
    }
  }
}
</style>
