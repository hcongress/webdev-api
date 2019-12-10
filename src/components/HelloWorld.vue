<template>
  <div>
    <v-row
          v-for="(item, i) in info"
          :key="i"
          class = "ma-5"
        >
      <v-card
    :loading="loading"
    class="mx-auto ma-5"
    max-width="1000"
    min-width="250"
  >
    <v-img
      aspect-ratio = "1.77"
      :src="item.imgMedium"
    ></v-img>

    <v-card-title>{{item.name}}</v-card-title>

    <v-card-text>
      <v-row
        align="center"
        class="mx-0"
      >
        <v-rating
          :value="item.stars"
          color= "#75c8ff"
          dense
          half-increments
          readonly
          size="14"
        ></v-rating>

        <div class="grey--text ml-4">{{item.stars}} ({{item.starVotes}})</div>
      </v-row>

      <div class="my-4 subtitle-1 black--text">
        {{item.location}} <br>
        Length: {{item.length}} miles  • Ascent: {{item.ascent}} ft • Descent: {{item.descent}} ft
      </div>

      <div>{{item.summary}} While the idea of skiing may inspire images of powdery snow, gorgeous vistas and steamy hot chocolate, it is important to remember that skiing is no walk in the park. It is, however, a thrilling sport that can satiate anyone's need for an adrenaline rush. If you've always wanted to try out skiing but have not yet had the opportunity to do so, this guide can help you get started. Keep in mind that while this article covers the basics of alpine ("downhill") skiing, it is not a substitute for actual lessons — read on and then go enroll in a class to begin to have ridiculous amounts of snowy fun!</div>
    </v-card-text>

    <v-divider class="mx-4"></v-divider>
    <v-card-actions>
      <v-btn
        color="#75c8ff"
        text
        @click="reserve"
      >
        Get Directions
      </v-btn>
    </v-card-actions>
    <v-card color= "#75c8ff">
      <v-card-title class="font-weight-medium white--text">Difficulty: {{item.difficulty}}</v-card-title>
    </v-card>
  </v-card>
  </v-row>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',

  data () {
    return {
      info: []
    }
  },
  backgroundColor: function (item) {
    let rating = item.difficulty
    if (rating === 'dblack') {
      return '#000000'
    } else if (rating === 'black') {
      return '#4a4a4a'
    } else if (rating === 'blueBlack') {
      return '#000d61'
    } else if (rating === 'blue') {
      return '#0022ff'
    } else {
      return '#00c91b'
    }
  },
  mounted () {
    axios.get('https://www.powderproject.com/data/get-trails?lat=39.8917&lon=-105.7631&maxDistance=200&key=200648940-e0f4d3e6dd5f91b90142df34f1899279')
      .then(response => {
        this.info = response.data.trails
      })
  }
}
</script>
