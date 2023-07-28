<template>
   <div>
      <p>{{ formattedDateTime }}</p>
   </div>
</template>

<script>
export default {
   props: {
      dateTimeString: {
         type: String,
         required: true,
      }
   },
   data() {
      return {
         formattedDateTime: ''
      }
   },
   methods: {
      formatDate() {
         const dateTime = new Date(this.dateTimeString);
         const day = dateTime.getDate();
         const month = this.getMonthText(dateTime.getMonth());
         const year = dateTime.getFullYear();
         const hours = dateTime.getHours();
         const minutes = this.addLeadingZero(dateTime.getMinutes());
         const ampm = hours >= 12 ? 'PM' : 'AM';
         this.formattedDateTime = `${day} ${month} ${year}, ${hours}:${minutes} ${ampm}`;
      },
      getMonthText(month) {
         const months = [
            'Januari', 'Februari', 'Maret', 'April', 'Mei', 'Juni',
            'Juli', 'Agustus', 'September', 'Oktober', 'November', 'Desember'
         ];
         return months[month];
      },
      addLeadingZero(number) {
         return number < 10 ? `0${number}` : number;
      },
   },
   mounted() {
      this.formatDate();
   }
}
</script>