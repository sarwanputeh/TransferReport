<script>
import Report from "@/components/Report.vue";

export default {
  name: "ReportView",
  components: {
    Report,
  }
}
</script>

<template>
  <div>
    <Report ContractNo="45123" LesseeName="SCG"  LesseeAddress="123 soi phahonyothin19"
      :ItemCheck="[0, 1, 0, 1, 0, 1, 0, 0, 1, 1, 1]"
      :ItemOther="['item 1', 'item 2', 'item 3', 'item 4']" 
      PICContact="Soonthorn" PICTel="02-7924500 #1202"/>
  </div>
</template>
