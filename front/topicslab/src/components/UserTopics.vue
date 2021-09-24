<template>
  <div>
  <TabView>
    <TabPanel header="Header I">
      <p>Content I</p>
    </TabPanel>
    <TabPanel header="Header II">
      <p>Content II</p>
    </TabPanel>
  </TabView>
  </div>
</template>

<script>
import TabView from 'primevue/tabview'
import TabPanel from 'primevue/tabpanel'

export default {
  components: {
    TabView,
    TabPanel
  }
}
</script>
