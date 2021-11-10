<template>
  <div class="home">
    <DefaultTheme>
      <Gantt :tasks="tasks" :links="links" :scales="scales" :columns="columns" />
    </DefaultTheme>
  </div>
</template>

<script>
import { Gantt, DefaultTheme } from "@dhtmlx/trial-vue-gantt";
import { columns, scales, tasks, links } from "../data";
import ganttConfig from './gantt.config.json';


export default {
  name: 'Home',
  components: {
    Gantt,
    DefaultTheme
  },
  data() {
    return {
      columns,
      scales,
      tasks,
      links,
      form: {
        begin: '2021-09-01',
        end: '2021-11-01',
        page: 1
      },
      dataSource: ganttConfig.data,
    }
  },
  // computed: {
  //   tasks() {
  //     return this.task
  //   }
  // },
  created() {
    // this.mapData();
  },
  methods: {
    mapData() {
      this.tasks = this.dataSource.filter((el) => el.organizer !== '').map((item, index) => {
        return {
          id: index,
          open: true,
          start_date: item.begin,
          end_date: item.end,
          text: item.organizer,
        }
      })
      console.log(this.tasks, 'tasks')
    }
  },
};
</script>

<style lang="sass">
.home
  height: 100vh 
</style>