<template>
<div>
  <h1 class="text-center">Study Tracker</h1>
  <div id="add-hours" class="card">
    <h2 class="card-header">Update Record</h2>
    <div class="card-body">

      <form>
        <div class="alert alert-danger" v-show="errors && errors.length > 0">
            <li v-for="error in errors" v-bind:key="error">{{ error }}  </li>
        </div>

        <div class="form-group">
          <label class="form-label" for="subject">What class?</label>
          <select class="form-control" v-model="subject">
              <option v-for="subject in subjects" v-bind:value="subject" v-bind:key="subject">{{ subject }}</option>
          </select>
        </div>
                  
        <div class="form-group">
            <!-- TODO change label message to include name of activity -->
          <label class="form-label" for="when">When did you do it?</label>
          <input id="when" class="form-control" type="date" v-model.lazy="when" >
        </div>

        <div class="form-group">
          <label class="form-label" for="howLong">How long were doing this?</label>
          <input id="howLong" class="form-control" v-model.number.lazy="howLong">
        </div>

        <div>
            <button class="btn btn-primary mt-2" type="button" @click="submit">Add record</button>
        </div>

      </form>
    </div>
  </div>
</div>
</template>

 
<script>
export default {
  name: 'RecordForm',
  data() {
    return {
      when: '',
      howLong: '',
      subject: '',
      subjects: [
        'math', 'drawing', 'programming'
      ],
      errors: [],
      record: []
    }
  },
  methods: {
    submit() 
    {
        this.errors = []
        if (this.whenLocal == 'Invalid Date' || this.whenLocal.getTime()> new Date().getTime() ) 
        {
            this.errors.push('Select a valid date, today or in the past')
        }
        if (typeof (this.howLong) != "number" || this.howLong <= 0) 
        {
            this.errors.push('The number of hours must be a number greater than zero.')
        }
        if (this.errors.length == 0) 
        {
          let record = {
              when: this.whenLocal,
              howLong: this.howLong,
              subject: this.subject
          }
          alert(record)
          return record
        }
    }
  },
  computed: 
    {
      whenLocal() 
      {
        let date = new Date(this.when)
        let timestamp = date.getTime() + (date.getTimezoneOffset() * 60 * 1000)
        let localDate = new Date(timestamp)
        return localDate
      }
    }
}
</script> 

<style scoped>

</style>