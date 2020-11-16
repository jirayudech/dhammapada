<template>
  <div>
<!--   <v-card
    :loading="loading"
    class="mx-auto my-12"
    max-width="800"
  > -->
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>

      <v-card-text>
      <v-row>
    <v-badge
      v-for="(word, index) in words" :key="index"
      :value="hover[index]"
      color="deep-purple accent-4"
      :content="word.thai"
      right
      transition="slide-x-transition"
    >
      <v-hover v-model="hover[index]">
        <v-chip>{{word.pali}}</v-chip>
      </v-hover>
    </v-badge>
<!--       <v-chip v-for="word in words" :key="word.id">{{word.pali}}</v-chip> -->
      </v-row>
    </v-card-text>
    <v-card-text>
      {{thai}}
    </v-card-text>
<!--     <v-card-actions>
      <v-btn
        color="deep-purple lighten-2"
        text
        @click="reserve"
      >
        Reserve
      </v-btn>
    </v-card-actions> -->
<!--   </v-card> -->
  <v-divider></v-divider>
  </div>
</template>
<script>
export default {
  name: 'Paragraph',
  props: {
    title: String,
    story: String,
    wak: String,
    pak: String,
    paragraph: String,
    thai: String
  },
  data: () => ({
    loading: false,
    hover: [],
    hover2: false,
    words: []
  }),
  mounted: function () {
    this.fetchStory(this.pak, this.wak, this.story, this.paragraph)
    let i
    for (i = 0; i < 100; i++) {
      this.hover[i] = false
    }
  },
  methods: {
    reserve () {
      this.loading = true

      setTimeout(() => (this.loading = false), 2000)
    },
    fetchStory (pak, wak, story, paragraph) {
      fetch(`https://sheet.best/api/sheets/433218c4-6b0a-41ce-9fab-280bebce3abf/tabs/db_word/search?story=${story}&wak=${wak}&pak=${pak}&paragraph=${paragraph}`)
        .then((response) => response.json())
        .then((data) => {
          console.log(data)
          this.words = data
        })
        .catch((error) => {
          console.error(error)
        })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
