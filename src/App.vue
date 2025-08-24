<script>

import FullCalendar from '@fullcalendar/vue3'
import dayGridPlugin from '@fullcalendar/daygrid'
import interactionPlugin from '@fullcalendar/interaction' 
import ruLocale from '@fullcalendar/core/locales/ru';
import esLocale from '@fullcalendar/core/locales/es';

export default {
  components: {
    FullCalendar 
  },


  data: function() {
    return {
    calendarOptions: {  
    plugins: [ dayGridPlugin, interactionPlugin ],  
    initialView: 'dayGridMonth',  
    dateClick: this.getDate,
    weekends: true,
    locale: ruLocale,
    events:  [
          { title: 'Задача 1', start: '2025-08-01' },
          { title: 'Задача 2', start: '2025-08-20' }
        ]
}  
  }  
  },
 methods: {
  getDate: function(arg){
  this.calendarOptions.events.push({title:`${arg.dateStr}`,start:new Date(`${arg.dateStr}`)})
  },
  changeLanguage: function() {
    return this.calendarOptions.locale =!this.calendarOptions.locale

  }
   }}
 
</script>

<template >
   <button @click="changeLanguage">Change Language</button>
    
 <FullCalendar :options='calendarOptions' />

</template>

<style >


</style>
