/* eslint-disable */
<template>
  <div style="padding: 10px; background: #f8f8f9">
    <Card
      :title="contest_name"
      icon="ios-trophy"
      padding="0"
      shadow
      style="width: 100%"
      :to="{path: '/gradeshow', query: {exam_id : exam_id}}"
    >
      <CellGroup>
        <Cell>
          <Icon type="md-calendar" />{{
            contest_date
          }}&nbsp;&nbsp;&nbsp;&nbsp;<Icon type="md-clock" />{{
            contest_time
          }}
          </Cell>
      </CellGroup>
    </Card>
  </div>
</template>
<script>
export default {
  props: ['contest_name', 'contest_date', 'contest_time', 'exam_id'],
  data () {
    return {
      informations: 'exam-informations',
      exam_date: 'xxxx-xx-xx',
      time_limit: 'xx:xx -- xx:xx'
    }
  }
}
</script>
