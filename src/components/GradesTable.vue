<template>
  <table class="grades">
    <thead>
      <tr>
        <td>Name</td>
        <td>Grade</td>
        <td>Points Earned</td>
        <td>Points Worth</td>
      </tr>
    </thead>
    <tbody>
      <Grade v-for="grade in grades" v-bind:key="grade.name" :grade="grade" />
      <Grade
        v-if="grades.length"
        :grade="{
          name: 'Data Summary',
          grade: arraySum(grades.map((ass) => ass.grade)),
          maxPoints: arraySum(grades.map((ass) => ass.maxPoints)),
        }"
      />
    </tbody>
  </table>
</template>

<script lang="ts">
import Grade from "./Grade.vue";
import type { GradeData } from "../models";

export default {
  props: {
    grades: Object as () => GradeData[]
  },
  components: {
    Grade
  },
  methods: {
    arraySum(arr: string[]) {
      return arr.reduce((a: any, b: any) => {
        return parseFloat(a) + parseFloat(b)
      }, 0);
    }
  }
}
</script>

<style lang="scss">
table.grades {
  border-collapse: collapse;
  width: 75%;
  font-size: 1.125rem;

  thead td {
    font-weight: 500;
  }

  tbody tr:last-of-type {
    font-weight: 600;
    background: rgba(0, 0, 0, 0.04);
  }

  td {
    padding: 0.8rem 0.8rem;
    border: 1px solid rgba(0, 0, 0, 0.3);
  }
}
</style>
