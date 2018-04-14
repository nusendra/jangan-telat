<template>
  <Page class="page">
    <ActionBar class="action-bar" title="Jangan Telat !!"/>

    <StackLayout>
      <Label text="End Time (h)" class="text"/>
      <TimePicker v-model="endTime"/>

      <Label text="Distance (km)" class="text"/>
      <TextField v-model="distance" keyboardType="number"/>

      <Label text="Start Time (h)" class="text"/>
      <TimePicker v-model="startTime"/>
      
      <Label :text="'Kecepatan : ' + result + ' km/h'" class="result"/>
    </StackLayout>

  </Page>
</template>

<script>
export default {
  data() {
    return {
      distance: 0,
      startTime: new Date(),
      endTime: new Date()
    }
  },
  computed: {
    result() {
      if (this.startTime.getTime() > this.endTime.getTime()){
        return 'Wrong Time !!'
      } else {
        var timeDiff = Math.abs(this.endTime.getTime() - this.startTime.getTime())/36e5
        return this.distance / timeDiff
      }
    }
  },
}
</script>

<style>
.text{
  font-size: 18;
  align-content: center;
}
.result{
  font-size: 30;
  align-content: center;
}
</style>
