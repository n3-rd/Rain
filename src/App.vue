<template>
  <router-view />

<q-dialog v-model="namePrompt" persistent>
      <q-card style="min-width: 350px">
        <q-card-section>
          <div class="text-h6">Hi there!, what's your name</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          <q-input dense v-model="userName" autofocus @keyup.enter="storeUserName" />
        </q-card-section>

        <q-card-actions align="right" class="text-primary">
          <q-btn flat label="Store Name" @click="storeUserName" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>

  <q-tabs
    class="tabs fixed-bottom q-py-md"
    indicator-color="transparent"
    active-color="primary"
  >
    <q-route-tab :ripple="false" icon="bar_chart" to="/Stats" exact />
    <q-route-tab :ripple="false" icon="bedtime" to="/" exact />
    <q-route-tab :ripple="false" icon="settings" to="/Settings" exact />
  </q-tabs>
</template>
<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "App",
  data(){
    return{
      namePrompt: false,
      userName: ''
    }
  },
  methods: {
    storeUserName: function(){
      localStorage.setItem('rainrUserName', this.userName);
      this.namePrompt = false
    }
  },
  created(){
    if(!localStorage.getItem('rainrUserName')){
      this.namePrompt = true
    }
  }
});
</script>
