<template>
<div>
  <p>table here</p>

<div class="card">
  <h2 class="card-header">Activity Record</h2>

  <div class="card-body">
    <!-- TODO display the number of records  -->
    <h3> {{ activityRecords.length }} record(s)</h3>

    <div id="records">
      <table class="table">
        <tr>
          <th>When</th>
          <th>How long?</th>
          <th>subject</th>
        </tr>
        <!-- TODO display one table row for each activityRecord  -->
        <!-- <tr v-for="record in activityRecords">
          <td>{{ record.when | shortDateFormat }}</td>
          <td>{{ record.howLong }}</td>
          <td>{{ record.subject }}</td>
              </tr> -->
          </table>
      </div>
  </div>
  </div>


  <div class="card">
    
    <h2 class="card-header">Summary</h2>

    <div class="card-body">
      <!-- TODO use computed property to display total hours -->
      <p>You have spent a total of {{totalHours}} hours, broken down as follows:</p>
      
      <!-- TODO computed property to display total for each type  
      <ul class="list-group list-group-flush">
          <li class="list-group-item" v-for="hours, subject in totalHoursBySubject">{{ subject }}: {{ hours }}</li>
      </ul>-->
    </div>
  </div>
</div>



</template>

<script>
//import RecordForm from '@/components/RecordForm'
export default {
  name: 'RecordTable',
  data() {
    return {
      activityRecords: []
    }
  },
  components: {
    //RecordForm
  },
  computed: {
    totalHours() {
      let total = 0
      if (this.activityRecords.length > 0){
          total = this.activityRecords.reduce(function (hoursAccumulator, currentRecord) {
              return hoursAccumulator + currentRecord.howLong
          }, 0)
      }
      return total
    
    },
    totalHoursBySubject() {
      let hoursBySubject = {}
      this.subjects.forEach(subject => {
        let totalForSubject = this.activityRecords
          .filter(function (record) { return record.subject === subject})
          .reduce(function (accumulator, current) {return accumulator + current.howLong }, 0)
        hoursBySubject[subject] = totalForSubject
      })
    return hoursBySubject
    }
  }
}

</script>
<style>

</style>