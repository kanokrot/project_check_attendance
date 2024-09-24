<script setup>
import { VCard, VCardText, VRow, VCol, VDialog, VTextField, VBtn, VForm } from 'vuetify/lib/components/index.mjs';
import { ref } from 'vue';

const currentPage = ref(1);
const totalPages = ref(10);
const dialog = ref(false);

const fetchData = (page) => {
  console.log(`Fetching data for page ${page}`);
};

const periodName = ref('');
const startTime = ref('');
const endTime = ref('');
const date = ref('');

const subClassPeriod = () => {
  console.log(`Period Name: ${periodName.value}, Start Time: ${startTime.value}, End Time: ${endTime.value}, Date: ${date.value}`);
  dialog.value = false;
};

const addClassPeriod = () => {

  periodName.value = '';
  startTime.value = '';
  endTime.value = '';
  date.value = '';

  dialog.value = true;
};

</script>

<template>
  <div style="display: flex; align-items: center;">
    <h3 style="font-size: 37px; margin-inline-start: 10px;">CP422101</h3>
    <h3 style="font-size: 14px;">Introduction to Computer Networking</h3>
  </div>
  <br />
  <div style="display: flex; justify-content: space-between;">
    <p style="font-size: 15px; text-align: start;"></p>
    <p style="font-size: 18px; text-align: end;">
      <a href="www.">AttendanceCheck</a> / <a href="attendance_page.html">Course</a><br />
      / <a href="attendance_page.html">CP422101 Introduction to Computer Networking</a> / <a href="attendance_page.html">Course
        Outline</a>
    </p>
  </div>

  <VCard class="mt-5" :style="{ backgroundColor: '#747070', color: '#fff' }">
    <VCardText>
      <div>
        <VBtn color="primary" @click="addClassPeriod" class="mr-2">
          <v-icon left>mdi-plus</v-icon>
          Add Class Period
        </VBtn>
        <VBtn color="primary" @click="$router.push('/student')">
          <v-icon left>mdi-account</v-icon>
          Student
        </VBtn>
      </div>

      <div style="margin-block-start: 10px;">
        <VCard :style="{ backgroundColor: '#D9D9D9', color: '#333', marginBottom: '10px' }">
          <VCardText style="inline-size: 100%;">
            <div style="display: flex; align-items: center; padding: 5px; font-size: 18px;">
              <span style="flex: 1; text-align: start;">Lec01: Course Outline</span>
              <span style="flex: 1;margin-inline-end: 10px; text-align: start; ">17/05/2024</span>
              <span style="flex: 1;margin-inline-end: 10px; text-align: start; ">14:30 - 16:00</span>

              <VBtn icon @click="showOptions" style="margin-inline-start: auto;" color="red">
                <v-icon>mdi-delete-forever</v-icon>
              </VBtn>
            </div>
          </VCardText>
        </VCard>

        <VCard :style="{ backgroundColor: '#D9D9D9', color: '#333', marginBottom: '10px' }">
          <VCardText style="inline-size: 100%;">
            <div style="display: flex; align-items: center; padding: 5px; font-size: 18px;">
              <span style="flex: 1; text-align: start;">Lec01: Course Outline</span>
              <span style="flex: 1; margin-inline-end: 10px; text-align: start;">17/05/2024</span>

              <span style="flex: 1; margin-inline-end: 10px; text-align : start; ">14:30 - 16:00</span>

              <VBtn icon @click="showOptions" style="margin-inline-start: auto;" color="red">
                <v-icon>mdi-delete-forever</v-icon>
              </VBtn>
            </div>
          </VCardText>
        </VCard>
      </div>

      <div class="mt-4 d-flex justify-center">
        <VPagination v-model="currentPage" :length="totalPages" :total-visible="5" @input="fetchData"
          style="color: white;" />
      </div>
    </VCardText>
  </VCard>

  <VDialog v-model="dialog" max-width="500px" max-height="90vh">
    <template #title>
      <h3>Add Class Period</h3>
    </template>
    <VCard>
      <VCardText>
        <VForm>
          <h2 style="text-align: center;">Class Period</h2>

          <VRow>
            <VCol>
              <VTextField v-model="periodName" label="Period Name" required />
            </VCol>
          </VRow>

          <VRow>
            <VCol>
              <VTextField v-model="startTime" label="Start Time" required type="time" />
            </VCol>
            <VCol>
              <VTextField v-model="endTime" label="End Time" required type="time" />
            </VCol>
          </VRow>

          <VRow>
            <VCol>
              <VTextField v-model="date" label="Date (mm/dd/yyyy)" required type="date" />
            </VCol>
          </VRow>

          <VCardActions>
            <VBtn color="primary" @click="subClassPeriod">Submit</VBtn>
            <VBtn @click="dialog = false">Cancel</VBtn>
          </VCardActions>
        </VForm>
      </VCardText>
    </VCard>
  </VDialog>

</template>
