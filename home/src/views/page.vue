<template>
  <div class="p-3 mb-2 bg-light text-dark" style='width: 100%; height: 99vh; overflow: hidden' v-on:keyup.enter='search()'>
    <div class=" d-flex align-items-center justify-content-center flex-column" style="margin-top: 35vh;">
      <div style='color: #585858; font-size: 7vh; font-weigth: 700' id='age'> {{ age }} </div>
      <div style='width: 40vh' class="input-group mb-3">
        <input id='searchfield' type="text" class="form-control" placeholder="Suchbegriff" aria-label="Recipient's username" aria-describedby="button-addon2">
        <div class="input-group-append">
          <button @click="search()" class="btn btn-outline-primary" type="button" id="button-addon2">
            <svg width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-search" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
                <path fill-rule="evenodd" d="M10.442 10.442a1 1 0 0 1 1.415 0l3.85 3.85a1 1 0 0 1-1.414 1.415l-3.85-3.85a1 1 0 0 1 0-1.415z"/>
                <path fill-rule="evenodd" d="M6.5 12a5.5 5.5 0 1 0 0-11 5.5 5.5 0 0 0 0 11zM13 6.5a6.5 6.5 0 1 1-13 0 6.5 6.5 0 0 1 13 0z"/>
              </svg>
          </button>
        </div>
      </div>
      </div>
  </div>
</template>

<script>

export default {
  name: 'page',
  data(){
    return{
      age: 0,
    }
  },
  mounted: function(){
    var birthday = this.$route.params.birthday.split('+').join(' ')
    setInterval(() => {
      const date1 = Date.parse(birthday)
      const date2 = new Date()
      this.age = ((((date2 - date1)) / 1000) / 31556952).toFixed(10)
    }, 111);
  },
  methods: {
    search: function(){
      const searchfield = document.getElementById('searchfield')
      var tosearch = searchfield.value.split(' ')
      location.replace('https://www.google.com/search?client=firefox-b-d&q=' + tosearch.join("+"))
    }
  }
};

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Grandstander');
#age {
    font-family: 'Grandstander', sans-serif;
}


</style>
