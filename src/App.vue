
<template>
  <div class="
      bg-gradient-to-tr
      from-emerald-500
      to-teal-300
      min-h-screen
      flex
      justify-center
    ">
    <div class="bg-white divide-y shadow-lg rounded-lg m-8">
      <div class="m-8">
        <!-- 上面 -->
        <div>
          <h1 class="
              text-emerald-400 text-2xl
              font-bold
              text-center
              tracking-wider
            ">
            BMI計算器
          </h1>
          <div class="mt-6">
            <label class="inline-block mb-1 text-gray-400">身高</label>
            <div class="px-3 py-1.5 border border-emerald-300 rounded-md">
              <input class="focus:outline-none mr-1.5" type="number" v-model="height" />
              <span class="shrink-0 text-emerald-400 select-none">公分</span>
            </div>
          </div>
          <div class="mt-6">
            <label class="inline-block mb-1 text-gray-400">體重</label>
            <div class="px-3 py-1.5 border border-emerald-300 rounded-md">
              <input class="focus:outline-none mr-1.5" type="number" v-model="weight" />
              <span class="shrink-0 text-emerald-400 select-none">公斤</span>
            </div>
          </div>
        </div>

        <div class="mt-6 text-center text-gray-400">BMI</div>
        <div class="mt-6 text-center text-gray-400">
          {{ bmi }}
        </div>
        <div class="
            mt-6
            py-1.5
            text-center
            bg-amber-200
            text-amber-600 text-lg
            font-bold
            ring-1 ring-amber-500/30
            rounded-md
            shadow-lg shadow-amber-200
          " v-if="result==='體重過輕'">
          你的體重是「過輕」
        </div>
        <div class="
            mt-6
            py-1.5
            text-center
            bg-green-200
            text-green-600 text-lg
            font-bold
            ring-1 ring-green-500/30
            rounded-md
            shadow-lg shadow-green-200
          " v-if="result==='體重正常'">
          你的體重是「正常」
        </div>
        <div class="
            mt-6
            py-1.5
            text-center
            bg-amber-200
            text-amber-600 text-lg
            font-bold
            ring-1 ring-amber-500/30
            rounded-md
            shadow-lg shadow-amber-200
          "  v-if="result==='過重'">
          你的體重是「過重」
        </div>
        <div class="
            mt-6
            py-1.5
            text-center
            bg-orange-200
            text-orange-600 text-lg
            font-bold
            ring-1 ring-orange-500/30
            rounded-md
            shadow-lg shadow-orange-200
          " v-if="result==='輕度肥胖'">
          你的體重是「輕度肥胖」
        </div>
        <div class="
            mt-6
            py-1.5
            text-center
            bg-pink-200
            text-pink-600 text-lg
            font-bold
            ring-1 ring-pink-500/30
            rounded-md
            shadow-lg shadow-pink-200
          "  v-if="result==='中度肥胖'">
          你的體重是「中度肥胖」
        </div>
        <div class="
            mt-6
            py-1.5
            text-center
            bg-red-200
            text-red-600 text-lg
            font-bold
            ring-1 ring-red-500/30
            rounded-md
            shadow-lg shadow-red-200
          " v-if="result==='重度肥胖'">
          你的體重是「重度肥胖」
        </div>
      </div>
      <!-- 下面 -->
      <div class="p-8">
        <ul class="space-y-2">
          <li class="flex text-yellow-400">
            <div class="w-24 font-bold">體重過輕</div>
            <div>BMI &lt; 18.5</div>
          </li>
          <li class="flex text-green-400">
            <div class="w-24 font-bold">正常範圍</div>
            <div>BMI &lt; 18.5</div>
          </li>
          <li class="flex text-yellow-400">
            <div class="w-24 font-bold">過重</div>
            <div>24≦BMI&lt;27</div>
          </li>
          <li class="flex text-orange-400">
            <div class="w-24 font-bold">輕度肥胖</div>
            <div>27≦BMI&lt;30</div>
          </li>
          <li class="flex text-pink-400">
            <div class="w-24 font-bold">中度肥胖</div>
            <div>30≦BMI&lt;35</div>
          </li>

          <li class="flex text-red-400">
            <div class="w-24 font-bold">重度肥胖</div>
            <div>BMI≧35</div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref,computed} from 'vue'
    const height=ref("")
    const weight=ref("")
    const bmi=computed(()=>{
      if (!weight.value || !height.value) {
        return "?";
      } else {
        return (
          weight.value /
          ((height.value / 100) * (height.value / 100))
        ).toFixed(1);
      }
    })
    const result=computed(()=>{
      const bmiValue = Number(bmi.value);
      if (bmiValue < 18.5) {
        return "過輕";
      } else if (bmiValue >= 18.5 && bmiValue < 24) {
        return "正常";
      } else if (bmiValue >= 24 && bmiValue < 27) {
        return "過重";
      } else if (bmiValue >= 27 && bmiValue < 30) {
        return "輕度肥胖";
      } else if (bmiValue >= 30 && bmiValue < 35) {
        return "中度肥胖";
      } else {
        return "重度肥胖";
      }
    })
</script>


