<template>
<div>
    <div class="tags flex flex--ai flex--jsb"  v-if="tags.length > 0">
        <div class="tags_container flex flex--ai">
            <div class="tag__pill flex flex--ai" v-for="(tag,index) in tags" :key="index">
                <div class="tag">{{tag}}</div>
                <div class="remove" v-on:click="filter(tag)"><img class="removex" src="../assets/images/icon-remove.svg" alt="removicon"></div>
            </div>
        </div>

        <button class="clear" v-on:click="clear()">Clear</button>
    </div> 
  </div>
</template>

<script>

export default {
  name: 'Tags',
  
  props: {
    tags: Array,
  },
  created() {
    
  },

  methods: {
    filter: function (tag) {
      this.$emit('clicked', tag)
    },

    clear: function () {
      this.$emit('clicked', "clearTags")
    },
  },
  
}
</script>
