<template>
  <div>
  <TabView>
    <TabPanel header="トピック">
      {{user.topics}}
    </TabPanel>
    <TabPanel header="コメント">
      {{user.comments}}
    </TabPanel>
  </TabView>
  </div>
</template>

<script>
import axios from '@/supports/axios'
import TabView from 'primevue/tabview'
import TabPanel from 'primevue/tabpanel'

export default {
  components: {
    TabView,
    TabPanel
  },
  props: {
    id: Number
  },
  data () {
    return {
      user: {}
    }
  },
  watch: {
    id () {
      if (this.id) {
        this.getUser()
      }
    }
  },
  methods: {
    getUser () {
      axios.get('/sanctum/csrf-cookie')
        .then(() => {
          axios.get(`/api/user/${this.id}`)
            .then((res) => {
              if (res.status === 200) {
                this.user.topics = res.data[0].topics[0].body
                this.user.comments = res.data[0].comments[0].body
                console.log(this.user)
              } else {
                console.log('取得失敗')
              }
            })
            .catch((err) => {
              console.log(err)
            })
        })
        .catch((err) => {
          alert(err)
        })
    }
  }
}
</script>
