<script setup lang="ts">
import StudentCard from './components/StudentCard.vue'
import type { Student } from './types'
import { ref, onMounted } from 'vue'
import StudentService from './services/StudentService'

const students = ref<Student[]>([])

onMounted(() => {
  StudentService.getStudents()
    .then((response) => {
      students.value = response.data
    })
    .catch((error) => {
      console.error('Error loading students:', error)
      // 如果API失败，使用模拟数据
      students.value = [
        { id: 1, name: 'John', surname: 'Doe', gpa: 3.5 },
        { id: 2, name: 'Jane', surname: 'Smith', gpa: 3.8 },
        { id: 3, name: 'Mike', surname: 'Johnson', gpa: 3.2 }
      ]
    })
})
</script>

<template>
  <div class="student-view">
    <h1>Student Information</h1>
    <div class="students">
      <StudentCard v-for="student in students" :key="student.id" :student="student" />
    </div>
  </div>
</template>

<style scoped>
.student-view {
  text-align: center;
  padding: 20px;
}
.students {
  display: flex;
  flex-direction: column;
  align-items: center;
}
h1 {
  margin-bottom: 30px;
  color: #2c3e50;
}
</style>