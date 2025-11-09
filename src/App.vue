<script setup lang="ts">
import { ref } from "vue";

// 반응형 상태 선언
const count = ref<number>(0);
const name = ref<string>("도연");
const colors = ref<string[]>(["red", "blue", "green"]);

const increment = (): void => {
  count.value++;
};
</script>

<template>
  <div class="p-6">
    <!-- 위쪽: 배경 없음 -->
    <p class="text-purple-700 text-lg mb-4 font-semibold">
      {{ name }}의 클릭 횟수 : {{ count }}
    </p>

    <!-- 아래쪽: 배경 있는 박스 -->
    <div class="bg-purple-100 p-4 rounded-xl shadow-sm">
      <!-- 버튼 -->
      <button
        @click="increment"
        class="bg-purple-500 hover:bg-purple-600 text-white px-3 py-1 rounded"
      >
        누른 횟수: {{ count }}
      </button>

      <!-- 조건부 렌더링 -->
      <p v-if="count >= 5" class="mt-3 text-gray-700">이제 꽤 많이 눌렀어요!</p>
      <p v-else class="mt-3 text-gray-600">
        아직 {{ 5 - count }}번 더 눌러보세요.
      </p>

      <!-- 입력창 -->
      <input
        v-model="name"
        placeholder="이름을 입력해주세요."
        class="border border-gray-300 rounded-md px-3 py-1 mt-3 w-full focus:ring-2 focus:ring-purple-300 focus:outline-none"
      />

      <!-- 리스트 -->
      <ul class="mt-3 list-disc list-inside text-purple-700">
        <li v-for="color in colors" :key="color">{{ color }}</li>
      </ul>
    </div>
  </div>
</template>
