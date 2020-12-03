<template>
  <div class="dashboard-container">
    <component :is="currentRole" />
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import adminDashboard from './admin'
import editorDashboard from './editor'

export default {
  name: 'Dashboard',
  components: { adminDashboard, editorDashboard },
  data() {
    return {
      currentRole: 'adminDashboard'
    }
  },
  computed: {
    ...mapGetters([
      'roles'
    ])
  },
  created() {
    console.log(this.$route.query.selected)
    if (this.$route.query.selected.includes('a')) {
      this.currentRole = 'editorDashboard'
    } else if ((this.$route.query.selected.includes('b'))) {
      this.currentRole = 'adminDashboard'
    }
  }
}
</script>
