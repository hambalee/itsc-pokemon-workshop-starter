<script setup lang="ts">
const props = defineProps<{ name: string; img: string }>(); // can not destructure

const emits = defineEmits<{
  (e: "viewDetail", name: string): void;
}>();

const onClickViewDetail = (name: string) => emits("viewDetail", name);
</script>

<template>
  <div class="card w-96 bg-base-100 shadow-xl">
    <figure>
      <img :src="props.img" alt="Shoes" />
    </figure>
    <div class="card-body">
      <h2 class="card-title capitalize">{{ props.name }}</h2>
      <div class="card-actions justify-end">
        <button
          class="btn btn-primary text-white"
          @click="onClickViewDetail(props.name)"
        >
          View Detail
        </button>
      </div>
    </div>
  </div>
</template>
