<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <!-- <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar> -->

<div class="row no-wrap shadow-1" style="height: 5px;">
        <q-toolbar class="col-8 col-md-7 bg-negative text-white q-pa-xs">
          <!-- Adjusted padding to q-pa-xs -->
        </q-toolbar>
        <q-toolbar class="col-4 col-md-5 bg-primary text-white q-pa-xs">
          <!-- Adjusted padding to q-pa-xs -->
        </q-toolbar>
      </div>

      <!-- Main Header Toolbar -->
      <q-toolbar class="bg-white text-primary q-pa-none" style="height: 100px;">
    
        <q-img
          src="Bangkok_Hospital_Phuket-logo-48EE6B9950-seeklogo.com.png" 
          :ratio="16/9"
          spinner-color="primary"
          spinner-size="82px"
          style="width: 270px; height: 75px; margin-left: 20px; margin-right: auto;"
        />
        

        <q-btn @click="handleLogin" to="/login" style="background: #F24C65; color: white"  no-caps label="Login" class="q-mr-md" />
        <q-btn @click="handleRegister" to="/register" style="background: #F24C65; color: white"  no-caps label="Register" class="q-mr-md" />
        &nbsp;&nbsp;
      </q-toolbar>
       
    </q-header>


    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
 
]

export default defineComponent({
  name: 'MainLayout',

  // components: {
  //   EssentialLink
  // },

  setup () {
    // const leftDrawerOpen = ref(false)

    return {
      // essentialLinks: linksList,
      // leftDrawerOpen,
      // toggleLeftDrawer () {
      //   leftDrawerOpen.value = !leftDrawerOpen.value
      // }
    }
  }
})
</script>
