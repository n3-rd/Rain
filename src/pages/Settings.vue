
<template>
  <div>
    <!-- <q-page> -->
    <div>
      
      <q-list>

        <div @click="changeUserName()" >
      <q-item class="cursor-pointer">
        <q-item-section avatar>
          <q-icon color="primary" name="person" size="lg"/>
        </q-item-section>

        <q-item-section class="text-h5 list-item">Change username</q-item-section>
      </q-item>
      </div>

      </q-list>

    </div>

    <!-- </q-page> -->
  </div>
</template>

<script>
export default {
  name: "Settings",
  data(){
    return{
      settings: [
        {name: 'change username', icon: 'person', action: function(){
                console.log(globalThis)
        }}
      ]
    }
  },
  methods: {
    changeUserName: function(){
      // console.log(this)
      // console.log('ew')
      console.log(this.$.parent.parent.data.namePrompt)
      this.$.parent.parent.data.namePrompt = true;
    }
  }
};
</script>
<style lang="scss">
.list-item{
   opacity: .8;
}
</style>
