<template>
  <div>
    <md-toolbar>
      <md-button class="md-icon-button" @click="toggleLeftSidenav">
        <md-icon>menu</md-icon>
      </md-button>
      <h2 class="md-title" style="flex: 1">Projectname</h2>
      <md-menu>
        <md-button class="md-icon-button" md-menu-trigger>
          <md-icon>more_vert</md-icon>
        </md-button>
        <md-menu-content>
          <md-menu-item @click="loginOut">Logout</md-menu-item>
        </md-menu-content>
      </md-menu>
    </md-toolbar>
    <md-sidenav class="md-left" ref="leftSidenav">
      <md-list>
        <template v-for="item in NAV">
          <md-list-item v-if="item.children">
            <md-icon>{{item.icon}}</md-icon>
            <span>{{item.name}}</span>
            <md-list-expand>
              <md-list v-for="it in item.children">
                <md-list-item class="md-inset" @click="closeLeftSidenav">
                  <router-link exact :to="it.path"> {{it.name}}</router-link>
                </md-list-item>
              </md-list>
            </md-list-expand>
          </md-list-item> 
          <md-list-item v-else @click="closeLeftSidenav">
            <router-link exact :to="item.path">
              <md-icon>{{item.icon}}</md-icon>
              <span>{{item.name}}</span>
            </router-link>
          </md-list-item> 
        </template>
      </md-list>
    </md-sidenav>
    <router-view></router-view>	
  </div>
</template>
<script>
const NAV = [{
  name: 'Examples',
  icon: 'equalizer',
  children: [{
    name: 'Example 1',
    path: '/example1'
  }, {
    name: 'Example 2',
    path: '/example2'
  }]
}, {
  name: 'Home',
  icon: 'home',
  path: '/home'
}]
export default {
  data () {
    return {
      NAV
    }
  },
  beforeCreate () {},
  created () {},
  beforeMount () {},
  mounted () {},
  beforeUpdate () {},
  updated () {},
  beforeDestory () {},
  destoryed () {},
  watch: {
    '$route' (nextRoute, route) {}
  },
  methods: {
    toggleLeftSidenav () {
      this.$refs.leftSidenav.toggle()
    },
    closeLeftSidenav () {
      this.$refs.leftSidenav.close()
    },
    loginOut () {
      this.$router.push('login')
    }
  }
}
</script>
