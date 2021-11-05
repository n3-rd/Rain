<template>
  <div>
    <!-- <q-page> -->
    <div>
        <q-list dark class="list">

      <q-item clickable v-ripple
      v-for="stat in stats" :key="stat.statTitle"
      >
        <q-item-section>
          <q-item-label class="text-h5 list-item">{{stat.statTitle}}</q-item-label>
          <q-item-label caption class="list-caption">{{stat.statValue}}</q-item-label>
        </q-item-section>
      </q-item>
        </q-list>
    </div>

    <!-- </q-page> -->
  </div>
</template>

<script>
export default {
  name: "Stats",
  data(){
    return{
      lastPlayedSound : localStorage.getItem('lastPlayedSound'),
      stats: [
        {
          statTitle: 'Last played sound', statValue: localStorage.getItem('lastPlayedSound')
        },
        {
          statTitle: 'Number of sounds played', statValue: localStorage.getItem('noPlayedSounds')
        }
      ],
    }
  }
};
</script>
<style lang="scss">
.list{
  .list-item{
    opacity: .8;
  }
.list-caption{
  font-size: 1.3rem;
  opacity: .7;
}
}
</style>
