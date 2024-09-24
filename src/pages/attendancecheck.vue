<script setup>
import { VCard } from 'vuetify/lib/components/index.mjs';
import { ref } from 'vue';

const currentPage = ref(1);
const totalPages = ref(10);


const fetchData = (page) => {
  console.log(`Fetching data for page ${page}`);
};

</script>
<template>
 <div style="display: flex; align-items: center;">
  <h3 style="font-size: 37px; margin-inline-end: 10px;">
    Attendance Check<br />
    <span style="font-size: 16px;">Lec 1: Course : 22/9/2567 14:30-16:00</span>
  </h3>
</div>

  <br />
  <div style="display: flex; justify-content: space-between;">
    <p style="font-size: 15px; text-align: start;"></p>
    <p style="font-size: 18px; text-align: end;">
        AttendanceCheck / Course<br />
        CP422022 Database Analysis /Attendance Check

    </p>
</div>

  
<VCard class="mt-5" :style="{ backgroundColor: '#747070', color: '#fff' }">
  <VCardText>
    <div style="display: flex;  align-items: center; justify-content: space-between; padding: 5px; font-size: 18px;">
      <span style="flex: 1; text-align: center;">Student :</span>
      <span style="flex: 1; text-align: center;">Name :</span>
      <span style="flex: 1; text-align: end;">Area :</span>
      <span style="flex: 1; text-align: end;">Section :</span>
      <span style="flex: 1; text-align: end;">On Time :</span>
      <span style="flex: 1; text-align: end;">Late :</span>
      <span style="flex: 1; text-align: end;">Absent :</span>
      <span style="flex: 1; text-align: end;">Serial Number :</span>
    </div>
    <VCard :style="{ backgroundColor: '#D9D9D9', color: '#333' }">
      <VCardText style="inline-size: 100%;">
  <div style="display: flex;align-items: center;  justify-content: space-between; padding: 5px; font-size: 16px;">
    <span style="flex: 1; text-align: center;">663380130-0</span>
    <span style="flex: 1; text-align: center;">รุ่งฤดี พึ่งสว่าง</span>
    <span style="flex: 1; text-align: end;">CP-CY</span>
    <span style="flex: 1; text-align: end;">Sec-2</span>
    
    <label style="flex: 1; text-align: end;">
      <input type="checkbox" /> 
    </label>
    <label style="flex: 1; text-align: end;">
      <input type="checkbox" />
    </label>
    <label style="flex: 1; text-align: end;">
      <input type="checkbox" />
    </label>

    <span style="flex: 1; text-align: end;">FE:01:AE:05:77</span>
  </div>
</VCardText>

      </VCard>

   
    
    <div class="mt-4 d-flex justify-center">
      <VPagination
        v-model="currentPage"
        :length="totalPages"
        :total-visible="5"
        @input="fetchData"
        style="color: white;"
      />
    </div>


  </VCardText>
</VCard>
</template>
