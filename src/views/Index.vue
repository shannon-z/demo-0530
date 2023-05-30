<template>
  <div class="index">
    <div>
      <div class="select-wrap">
        <el-select
          v-model="selections"
          placeholder="请选择"
          style="width: 200px"
        >
          <el-option
            v-for="item in selectionsList"
            :value="item.value"
            :label="item.label"
            :key="item.value"
            :disabled="true"
            @change="handleSelect"
          >
            <div>{{ item.label }}</div>
            <div>222222</div>
          </el-option>
        </el-select>
      </div>
      <div class="left-arrow-wrap"></div>
      <div class="selection-wrap">
        <div class="selection-wrap-title"></div>
        <div class="selections-items-content">
          <div class="selection-item">
            <div class="selection-item-title"></div>
            <div class="selection-item-opt"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Index",
  data() {
    return {
      selectionsList: [
        {
          label: "111",
          value: "111",
        },
        {
          label: "112",
          value: "112",
        },
        {
          label: "113",
          value: "113",
        },
      ],
      selections: [],
    }
  },
  methods: {
    handleSelect(e) {
      e.preventDefault()
    },
  },
}
</script>

<style>
</style>
