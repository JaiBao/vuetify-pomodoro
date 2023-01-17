<template lang="pug">
v-row.bg-blue(color="yellow")#settings
  v-col.bg-blue(cols="12")
    h1.text-center 設定
  v-col(cols="12")
    v-table.bg-blue
      thead.bg-blue
        tr
          th 名稱
          th 試聽
          th 選擇
      tbody.bg-blue
        //- tr(v-for="alarm in settings.alarms" :key="alarm.id")
        tr(v-for="alarm in alarms" :key="alarm.id")
          td {{ alarm.name }}
          td
            audio(:src="alarm.file" controls)
          td
            v-radio-group(v-model="selectedAlarms")
              v-radio(:value="alarm.id")
</template>

<script setup>
import { useSettingsStore } from '@/stores/settings'
import { storeToRefs } from 'pinia'

const settings = useSettingsStore()
const { alarms, selectedAlarms } = storeToRefs(settings)
</script>
<style lang="css" src="../css/style.css" scoped></style>
