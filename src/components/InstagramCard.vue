<template>

      <div class="card text-center">
        <div class="card-header text-left">
          {{ info.title }}
        </div>
        <div class="card-body">
          <img @click="change" class="card-img-top" :src="info.url" alt="Maznusmo s unsplasha i bilo bi lijepo da napisemo cija je slika">
        </div>
        <div class="container">
          <div class="row">
            <div class="col-6">
            <div class="card-footer text-left">
             {{ info.time }}
            </div>
            </div>
            <div class="col-6">
            <div class="card-footer text-right">
               {{info.user}}
            </div>
            </div>
          </div>
        </div>
      </div>

</template>

<script>
export default {
  props: ["info"],

  methods: {
    change() {
      this.info.time = 'Fetching...'
      fetch(`https://source.unsplash.com/1600x900`).then((response) => {   
        console.log(response)
        this.info.url = response.url
        this.info.time = 'Done.'
      }) 
    }
  }
}
</script>

<style lang="scss" scoped>
  img:hover {
    cursor: pointer;
  }
</style>