<template>
  <v-card
    :loading="loading"
    class="mx-auto my-12"
    max-width="800"
  >
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-img
      height="250"
      src="https://i.ytimg.com/vi/12_VDwh25Qw/maxresdefault.jpg"
    ></v-img>

    <v-card-title>๑. จกฺขุปาลตฺเถรวตฺถุ.</v-card-title>

        <v-card-text>
      <v-row>
      <v-badge
      :value="hover1"
      color="deep-purple accent-4"
      content="อ. พระธรรมเทศนา"
      left
      transition="slide-x-transition"
    >
      <v-hover v-model="hover1">
        <v-chip>ธมมฺเทสนา</v-chip>
      </v-hover>
    </v-badge>
    <v-badge
      :value="hover2"
      color="deep-purple accent-4"
      content="ตรัสแล้ว"
      left
      transition="slide-x-transition"
    >
      <v-hover v-model="hover2">
        <v-chip>ภาสิตาติ.</v-chip>
      </v-hover>
    </v-badge>
      <v-chip v-for="word in story" :key="word.id">{{word.pali}}</v-chip>
      </v-row>
    </v-card-text>
    <v-card-text>
ได้ยินว่า(อ.เศรษฐี)ชื่อว่ามหาสุวรรณเป็นผู้มีขุมทรัพย์ เป็นผู้มั่งคั่ง เป็นผู้มีทรัพย์มาก เป็นผู้มีโภคมาก เป็นผู้มีบุตรหามิได้ ได้มีแล้ว ในเมืองชื่อว่า สาวัติถี ฯ
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
  </v-card>
</template>
<script>
export default {
  name: 'Story',
  props: {
    title: String
  },
  data: () => ({
    loading: false,
    hover1: false,
    hover2: false,
    story: []
  }),
  mounted: function () {
    this.fetchStory()
  },
  methods: {
    reserve () {
      this.loading = true

      setTimeout(() => (this.loading = false), 2000)
    },
    fetchStory () {
      // this.story = []
      // this.story = await fetch('https://sheet.best/api/sheets/433218c4-6b0a-41ce-9fab-280bebce3abf/tabs/db/search?story=1&wak=1&pak=1&paragraph=3')
      fetch('https://sheet.best/api/sheets/433218c4-6b0a-41ce-9fab-280bebce3abf/tabs/db/search?story=1&wak=1&pak=1&paragraph=3')
        .then((response) => response.json())
        .then((data) => {
          console.log(data)
          this.story = data
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
