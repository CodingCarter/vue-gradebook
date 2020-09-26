<template>
  <h1>Your Gradebook</h1>
  <h2>Here are your latest and (hopefully) greatest grades!</h2>
  <GradesTable :grades="grades" />
  <GradeForm :addGrade="addGrade" />
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";
import GradesTable from "./components/GradesTable.vue";
import GradeForm from "./components/GradeForm.vue";
import type { GradeData } from "./models";

export default defineComponent({
  name: "App",
  components: {
    GradesTable,
    GradeForm
  },
  setup() {
    const grades = reactive([] as GradeData[]);

    function addGrade(grade: GradeData) {
      grades.push(grade);
    }

    return { grades, addGrade };
  },
});
</script>

<style lang="scss">
body {
  margin: 0;
  min-height: 100vh;
  width: 100%;
}

#app {
  display: flex;
  flex-direction: column;
  font-family: "Nunito";
  padding: 3rem;
  color: #545e75;

  h1,
  h2 {
    color: #304d6d;
    margin: 0;
  }

  h1 {
    font-size: 3.75rem;
    margin-bottom: 0.2rem;
  }

  h2 {
    font-weight: 500;
    font-size: 1.5rem;
    margin-bottom: 1.2rem;
  }
}
</style>
