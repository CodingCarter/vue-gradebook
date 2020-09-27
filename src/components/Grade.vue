<template>
  <tr>
    <td v-text="grade.name" />
    <td>{{ formatGrade(grade.grade, grade.maxPoints) }}%</td>
    <td v-text="grade.grade" />
    <td v-text="grade.maxPoints" />
  </tr>
</template>

<script lang="ts">
import type { GradeData } from "../models";

export default {
  props: {
    grade: Object as () => GradeData, // Thanks @mmitchellgarcia on Medium
  },
  methods: {
    formatGrade(grade: number, maxPoints: number) {
      return Math.floor(grade / maxPoints * 1000 + .5) / 10;
    }
  }
};
</script>
