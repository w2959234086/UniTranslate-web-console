<template>
  <el-row>
    <el-form-item label="Key" class="el-col-sm-12 p5px">
      <el-input type="text" v-model="props.config.key"></el-input>
    </el-form-item>
    <el-form-item label="Model" class="el-col-sm-12 p5px">
      <el-select
        v-model="props.config.model"
        placeholder="please select your zone"
      >
        <el-option label="gpt-3.5-turbo-0125" value="gpt-3.5-turbo-0125" />
        <el-option label="gpt-4-turbo" value="gpt-4-turbo" />
        <el-option label="gpt-3.5-turbo" value="gpt-3.5-turbo" />
      </el-select>
    </el-form-item>
  </el-row>
</template>

<script setup lang="ts">
import { defineProps, defineEmits, ref, watch } from "vue";
import type { ChatGPTConfig as configType } from "@/types/props";

const emit = defineEmits(["update:config"]);

const props = defineProps({
  config: {
    type: Object as () => configType,
    required: true,
  },
});

const config = ref<configType>();

config.value = props.config;

watch(config, (newVal) => {
  emit("update:config", newVal);
});
</script>
