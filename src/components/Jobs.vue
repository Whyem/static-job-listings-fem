<template>
  <div class="container" v-bind:class = "(tags.length > 0)?'':'pt'">
     <Tags :tags="tags" @clicked="onClickTag"/>
     <Job v-for="job in jobs" :key="job.id" :job="job" @clicked="onClickJob"/>
  </div>
</template>

<script>
import Tags from './Tags.vue'
import Job from './Job.vue'

export default {
  name: 'Jobs',
  components:{
    Job,
    Tags
  },
  data() {
    return {
      tags:[],
      jobs:[],
      myjson: [
        {
          "id": 1,
          "company": "Photosnap",
          "logo": require("@/assets/images/photosnap.svg"),
          "new": true,
          "featured": true,
          "position": "Senior Frontend Developer",
          "role": "Frontend",
          "level": "Senior",
          "postedAt": "1d ago",
          "contract": "Full Time",
          "location": "USA Only",
          "languages": ["HTML", "CSS", "JavaScript"],
          "tools": []
        },
        {
          "id": 2,
          "company": "Manage",
          "logo": require("@/assets/images/manage.svg"),
          "new": true,
          "featured": true,
          "position": "Fullstack Developer",
          "role": "Fullstack",
          "level": "Midweight",
          "postedAt": "1d ago",
          "contract": "Part Time",
          "location": "Remote",
          "languages": ["Python"],
          "tools": ["React"]
        },
        {
          "id": 3,
          "company": "Account",
          "logo": require("@/assets/images/account.svg"),
          "new": true,
          "featured": false,
          "position": "Junior Frontend Developer",
          "role": "Frontend",
          "level": "Junior",
          "postedAt": "2d ago",
          "contract": "Part Time",
          "location": "USA Only",
          "languages": ["JavaScript"],
          "tools": ["React", "Sass"]
        },
        {
          "id": 4,
          "company": "MyHome",
          "logo": require("@/assets/images/myhome.svg"),
          "new": false,
          "featured": false,
          "position": "Junior Frontend Developer",
          "role": "Frontend",
          "level": "Junior",
          "postedAt": "5d ago",
          "contract": "Contract",
          "location": "USA Only",
          "languages": ["CSS", "JavaScript"],
          "tools": []
        },
        {
          "id": 5,
          "company": "Loop Studios",
          "logo": require("@/assets/images/loop-studios.svg"),
          "new": false,
          "featured": false,
          "position": "Software Engineer",
          "role": "Fullstack",
          "level": "Midweight",
          "postedAt": "1w ago",
          "contract": "Full Time",
          "location": "Worldwide",
          "languages": ["JavaScript"],
          "tools": ["Ruby", "Sass"]
        },
        {
          "id": 6,
          "company": "FaceIt",
          "logo": require("@/assets/images/faceit.svg"),
          "new": false,
          "featured": false,
          "position": "Junior Backend Developer",
          "role": "Backend",
          "level": "Junior",
          "postedAt": "2w ago",
          "contract": "Full Time",
          "location": "UK Only",
          "languages": ["Ruby"],
          "tools": ["RoR"]
        },
        {
          "id": 7,
          "company": "Shortly",
          "logo": require("@/assets/images/shortly.svg"),
          "new": false,
          "featured": false,
          "position": "Junior Developer",
          "role": "Frontend",
          "level": "Junior",
          "postedAt": "2w ago",
          "contract": "Full Time",
          "location": "Worldwide",
          "languages": ["HTML", "JavaScript"],
          "tools": ["Sass"]
        },
        {
          "id": 8,
          "company": "Insure",
          "logo": require("@/assets/images/insure.svg"),
          "new": false,
          "featured": false,
          "position": "Junior Frontend Developer",
          "role": "Frontend",
          "level": "Junior",
          "postedAt": "2w ago",
          "contract": "Full Time",
          "location": "USA Only",
          "languages": ["JavaScript"],
          "tools": ["Vue", "Sass"]
        },
        {
          "id": 9,
          "company": "Eyecam Co.",
          "logo": require("@/assets/images/eyecam-co.svg"),
          "new": false,
          "featured": false,
          "position": "Full Stack Engineer",
          "role": "Fullstack",
          "level": "Midweight",
          "postedAt": "3w ago",
          "contract": "Full Time",
          "location": "Worldwide",
          "languages": ["JavaScript", "Python"],
          "tools": ["Django"]
        },
        {
          "id": 10,
          "company": "The Air Filter Company",
          "logo": require("@/assets/images/the-air-filter-company.svg"),
          "new": false,
          "featured": false,
          "position": "Front-end Dev",
          "role": "Frontend",
          "level": "Junior",
          "postedAt": "1mo ago",
          "contract": "Part Time",
          "location": "Worldwide",
          "languages": ["JavaScript"],
          "tools": ["React", "Sass"]
        }
      ],
    }
  },

  props: {
    msg: String
  },
  created() {
    this.jobs = this.updateJobs(this.myjson,this.tags);
  },

  methods: {
    updateJobs: function(jobs,tags){
      console.log(tags);
      
      var newjobs = [];
      
      if(tags.length === 0){
        return jobs;
      }

      jobs.forEach(job => {
        var job_tags = [job.role,job.level,...job.languages];
        var all_in = true;
        
        for (let i = 0; i < tags.length; i++) {
          if(!job_tags.includes(tags[i])){
            all_in = false;
          }          
        }
        
        if(all_in){
          newjobs.push(job);
        }
        
      });

      return newjobs;
    },

    onClickJob: function(value) {
      if(!this.tags.includes(value)){
        this.tags.push(value);
        this.jobs = this.updateJobs(this.myjson,this.tags);
      }
    },

    onClickTag: function(value) {
        if(value == "clearTags"){
          this.tags = [];
        }
        else{
          this.tags = this.tags.filter(function(item) {
            return item !== value
          });
        }
        this.jobs = this.updateJobs(this.myjson,this.tags);
      }
    
  },
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
