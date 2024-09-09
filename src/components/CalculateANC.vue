<script setup>
  import { ref } from 'vue';
  let masks = ref({ modelValue: 'YYYY-MM-DD', });

</script>

<script>
  export default {
    data() {
      return {
        title_name: 'เยี่ยมหลังคลอด',
        dateNow:"",
        birthday: 'ยังไม่ได้เลือกวันที่',
        visit1_start: '',
        visit1_end: '',
        visit2_start: '',
        visit2_end: '',
      }
    },
    mounted() {
    
    },
    methods: {
      calculateData() {
        const dateSelect = this.dateNow;
   

        if( dateSelect == "" ) {
          console.log("invalid");
        } else if (dateSelect == null) {
          this.visit1_s = "";
          this.visit1_e = "";
          this.visit2_s = "";
          this.visit2_e = "";
        } else {
              
          const visit1_s = this.dateNow;
          const visit1_e = this.dateNow;
          const visit2_s = this.dateNow;
          const visit2_e = this.dateNow;
          
          const dateConvert = dateSelect.toLocaleDateString('th-TH', {
            year: 'numeric',
            month: 'long',
            day: 'numeric',
          })

          this.birthday = dateConvert;
          // console.log(dateConvert);

          // visit1 begin
          this.visit1_start = visit1_s.setDate(visit1_s.getDate() + 8);
          this.visit1_start = visit1_s.toLocaleDateString('th-TH', {
            year: 'numeric',
            month: 'long',
            day: 'numeric',
          })
          this.visit1_end = visit1_e.setDate(visit1_e.getDate() + 6);
          this.visit1_end = visit1_e.toLocaleDateString('th-TH', {
            year: 'numeric',
            month: 'long',
            day: 'numeric',
          })
          // visit1 end
          // visit2 begin
          this.visit2_start = visit2_s.setDate(visit2_s.getDate() + 1);
          this.visit2_start = visit2_s.toLocaleDateString('th-TH', {
            year: 'numeric',
            month: 'long',
            day: 'numeric',
          })

          this.visit2_end = visit2_e.setDate(visit2_e.getDate() + 15);
          this.visit2_end = visit2_e.toLocaleDateString('th-TH', {
            year: 'numeric',
            month: 'long',
            day: 'numeric',
          })
          // visit2 end
          
        }
      }
    },
  }
</script>

<template>
  <!-- nav bar -->
  <div class="flex item-center navbar bg-white shadow rounded-3xl rounded-tl-none rounded-tr-none p-0 px-4 mb-5">
    <div class="navbar-start">
    </div>
    <div class="navbar-center">
      <div class="text-lg font-bold text-slate-600">{{ title_name }}</div>
    </div>
    <div class="navbar-end">
    </div>
  </div>
  <!-- nav bar -->
  
  <div class="">
    <svg width="100%" height="100%" id="svg" viewBox="0 0 1440 690" xmlns="http://www.w3.org/2000/svg" class="mt-32"><path d="M 0,700 L 0,131 C 100.02820512820514,139.46153846153845 200.0564102564103,147.92307692307693 275,139 C 349.9435897435897,130.07692307692307 399.802564102564,103.76923076923077 474,100 C 548.197435897436,96.23076923076923 646.7333333333335,115.00000000000001 729,116 C 811.2666666666665,116.99999999999999 877.2641025641024,100.23076923076923 953,118 C 1028.7358974358976,135.76923076923077 1114.2102564102565,188.07692307692307 1197,196 C 1279.7897435897435,203.92307692307693 1359.8948717948717,167.46153846153845 1440,131 L 1440,700 L 0,700 Z" stroke="none" stroke-width="0" fill="#ffffff" fill-opacity="0.4" class="transition-all duration-300 ease-in-out delay-150 path-0"></path><path d="M 0,700 L 0,306 C 73.83589743589741,316.5051282051282 147.67179487179482,327.0102564102564 241,332 C 334.3282051282052,336.9897435897436 447.14871794871794,336.4641025641026 523,322 C 598.851282051282,307.5358974358974 637.7333333333333,279.1333333333333 714,267 C 790.2666666666667,254.86666666666665 903.9179487179488,259.00256410256407 986,267 C 1068.0820512820512,274.99743589743593 1118.5948717948718,286.8564102564103 1189,294 C 1259.4051282051282,301.1435897435897 1349.702564102564,303.57179487179485 1440,306 L 1440,700 L 0,700 Z" stroke="none" stroke-width="0" fill="#ffffff" fill-opacity="0.53" class="transition-all duration-300 ease-in-out delay-150 path-1"></path><path d="M 0,700 L 0,481 C 94.0205128205128,501.1435897435897 188.0410256410256,521.2871794871794 265,511 C 341.9589743589744,500.71282051282054 401.8564102564103,459.9948717948718 475,461 C 548.1435897435897,462.0051282051282 634.5333333333332,504.73333333333335 708,499 C 781.4666666666668,493.26666666666665 842.0102564102565,439.0717948717949 922,427 C 1001.9897435897435,414.9282051282051 1101.425641025641,444.97948717948714 1191,461 C 1280.574358974359,477.02051282051286 1360.2871794871794,479.01025641025643 1440,481 L 1440,700 L 0,700 Z" stroke="none" stroke-width="0" fill="#ffffff" fill-opacity="1" class="transition-all duration-300 ease-in-out delay-150 path-2"></path></svg>
    <img class="image-full absolute top-[-15px] p-16" src="../assets/images/MomAndBaby.svg">
  </div>
  
  <div class="p-0">
    <div class="bg-white flex flex-col items-center shadow pt-5">
      
      <div class="w-full bg-white px-4">
        <div class="px-0 py-5">
          <div class="flex flex-row items-center font-bold text-slate-500 text-lg px-3"> ปฏิทินเลือกวันที่</div>
          
          <VDatePicker @click="calculateData()" class="mt-2" locale="th-TH" v-model="dateNow" :masks="masks" expanded />

          
        </div>
      </div>

    </div>

    <div class="relative">
      
      <div class="rotate-180">
        <svg width="100%" height="100%" id="svg" viewBox="0 0 1440 690" xmlns="http://www.w3.org/2000/svg" class=""><path d="M 0,700 L 0,131 C 100.02820512820514,139.46153846153845 200.0564102564103,147.92307692307693 275,139 C 349.9435897435897,130.07692307692307 399.802564102564,103.76923076923077 474,100 C 548.197435897436,96.23076923076923 646.7333333333335,115.00000000000001 729,116 C 811.2666666666665,116.99999999999999 877.2641025641024,100.23076923076923 953,118 C 1028.7358974358976,135.76923076923077 1114.2102564102565,188.07692307692307 1197,196 C 1279.7897435897435,203.92307692307693 1359.8948717948717,167.46153846153845 1440,131 L 1440,700 L 0,700 Z" stroke="none" stroke-width="0" fill="#ffffff" fill-opacity="0.4" class="transition-all duration-300 ease-in-out delay-150 path-0"></path><path d="M 0,700 L 0,306 C 73.83589743589741,316.5051282051282 147.67179487179482,327.0102564102564 241,332 C 334.3282051282052,336.9897435897436 447.14871794871794,336.4641025641026 523,322 C 598.851282051282,307.5358974358974 637.7333333333333,279.1333333333333 714,267 C 790.2666666666667,254.86666666666665 903.9179487179488,259.00256410256407 986,267 C 1068.0820512820512,274.99743589743593 1118.5948717948718,286.8564102564103 1189,294 C 1259.4051282051282,301.1435897435897 1349.702564102564,303.57179487179485 1440,306 L 1440,700 L 0,700 Z" stroke="none" stroke-width="0" fill="#ffffff" fill-opacity="0.53" class="transition-all duration-300 ease-in-out delay-150 path-1"></path><path d="M 0,700 L 0,481 C 94.0205128205128,501.1435897435897 188.0410256410256,521.2871794871794 265,511 C 341.9589743589744,500.71282051282054 401.8564102564103,459.9948717948718 475,461 C 548.1435897435897,462.0051282051282 634.5333333333332,504.73333333333335 708,499 C 781.4666666666668,493.26666666666665 842.0102564102565,439.0717948717949 922,427 C 1001.9897435897435,414.9282051282051 1101.425641025641,444.97948717948714 1191,461 C 1280.574358974359,477.02051282051286 1360.2871794871794,479.01025641025643 1440,481 L 1440,700 L 0,700 Z" stroke="none" stroke-width="0" fill="#ffffff" fill-opacity="1" class="transition-all duration-300 ease-in-out delay-150 path-2"></path></svg>
      </div>
      
      <div class=" pt-48">
        <div class="px-4 absolute top-0 w-full">
          <div class="flex flex-row items-center font-bold text-slate-500 text-lg px-3"> แปลผลวันนัด</div>

          <div class="border-2 border-dashed bg-white/65 rounded-3xl p-4 mb-6 mt-2">
            <div class="text-center">
              <p class="font-bold text-slate-500 text-lg">วันที่คลอด</p>
              <p class="">{{ birthday }}</p>
            </div>

            <hr class="my-3">
            
            <div class="text-center mt-4">
              <p class="font-bold text-slate-500 text-lg">นัดเยี่ยมครั้งที่ 1</p>
              <p class="">ระหว่างวันที่</p>
              <p class="">{{ visit1_start }} - {{ visit1_end }}</p>
            </div>

            <hr class="my-3">

            <div class="text-center mt-4">
              <p class="font-bold text-slate-500 text-lg">นัดเยี่ยมครั้งที่ 2</p>
              <p class="">ระหว่างวันที่</p>
              <p class="">{{ visit2_start }} - {{ visit2_end }}</p>
            </div>
          </div>

        </div>
      </div>

    </div>

  </div>
</template>

<style scoped></style>