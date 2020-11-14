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
        <v-chip>ภาสติาติ.</v-chip>
      </v-hover>
    </v-badge>
      </v-row>
    </v-card-text>
    <v-card-text>
(อันพระศาสดา) ตรัสแล้ว ในท่ีไหน ดังนี้ฯ
(อ. อันตอบ ว่า อ. พระธรรมเทศนา นี้ อัน พระศาสดา ตรัสแล้ว)
ในเมืองช่ือว่า สาวัต ถี (ดังนี้) ฯ
(อ. อันถาม ว่า อ. พระธรรมเทศนา นี้ อันพระศาสดา)
ทรงปรารภซึ่งใคร(ตรัสแล้วในเมืองชื่อว่าสาวตัถี)ดังนี้ฯ (อ.อันตอบว่าอ.พระธรรมเทศนานี้อันพระศาสดา ทรงปรารภ)ซึ่งพระเถระชื่อว่าจกัขบุาล(ตรัสแล้วในเมืองช่ือว่า
สาวัตถีดงันี้) ฯ
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
    hover2: false
  }),
  methods: {
    reserve () {
      this.loading = true

      setTimeout(() => (this.loading = false), 2000)
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
