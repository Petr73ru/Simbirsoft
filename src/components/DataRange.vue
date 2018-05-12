<template lang="jade">
  div
    h1 Enter time iterval
    label First date:
    input( type='date' v-model='f_date' )
    label End date:
    input( type='date' v-model='e_date')
    p(v-text='this.f_date')
    p(v-text='this.e_date')
    button( @click='cheak_time') Submit
</template>
<script lang="coffee">
export default
  data : () =>
    f_date   : null
    e_date   : null
  methods :
    cheak_time :  ()->
      if this.f_date == null or this.e_date == null
        return alert 'You need to set the interval!'
      f_date = this.f_date.split('-')
      e_date = this.e_date.split('-')
      if this.cheaker(0, f_date, e_date)
        console.log 'Interval is correct.'
      else console.log 'Interval is incorrect.'

    cheaker : (i, f_date, e_date)->
      if i == 3 then return false

      if e_date[i] > f_date[i]
        return true
      else if e_date[i] < f_date[i]
        return false
      else return this.cheaker(++i, f_date, e_date)
</script>
<style lang="stylus" scoped>
  div
    border 1px solid red
  h1
    color red
</style>
