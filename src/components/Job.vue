<template>
  <div class="job fd-bm flex--ai flex--jsb" v-bind:class = "(job.featured)?'featured_job':''">
    <div class="left fd-bm flex--ai">
      <img :src="job.logo" class="logo" alt="Logo">
      <div class="infos">
        <div class="infos_text flex flex--ai">
          <h3 class="company">{{job.company}}</h3>
          <h3 v-if="job.new" class="new">NEW!</h3>
          <h3 v-if="job.featured" class="featured">FEATURED</h3>
        </div>

        <h1 class="position">{{job.position}}</h1>

        <div class="coords flex flex--ai flex--jsa">
          <p>{{job.postedAt}}</p>
          <p>&bull;</p>
          <p>{{job.contract}}</p>
          <p>&bull;</p>
          <p>{{job.location}}</p>
        </div>
      </div>
    </div>

    <div class="right flex flex-ai">
      <p class="specs" v-on:click="filter(job.role)">{{job.role}}</p>
      <p class="specs" v-on:click="filter(job.level)">{{job.level}}</p>
      <p  v-for="(language,index) in job.languages" :key="index" class="specs" v-on:click="filter(language)">{{language}}</p>
    </div>
    
    <p></p>
    
  </div>
</template>

<script>

export default {
  name: 'Job',
  components:{
    
  },
  
  props: {
    job: Object
  },

  methods: {
    filter: function (tag) {
      this.$emit('clicked', tag)
    },
  },

}
</script>
