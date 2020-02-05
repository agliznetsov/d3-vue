<template>
  <div>
    <h1>Circle Pack in D3</h1>
    <h2>{{ msg }}</h2>
    <svg :height='height' :width='width'>
      <g transform="translate(50,50)">
        <circle
          v-for="c in output"
          :key="c.id"
          :r="c.r"
          :cx="c.x"
          :cy="c.y"
          :fill="c.fill"
          :stroke="c.stroke"
        >
        </circle>
      </g>
    </svg>
  </div>
</template>

<script>

export default {
  name: "PackChart",
  props: ["tweetData"],
  data() {
    return {
      msg: "👋 from the Chart Component",
      height: 600,
      width: 600
    };
  },
  created() {
  },
  methods: {
  },
  computed: {
    output() {
      var data = [];
      var x = 0;
      var y = 0;
      this.tweetData.forEach(it => {
        var r = it.retweets.length * 10;
        data.push({r:r, x:x, y:y, fill:"#5EAFC6", stroke:"grey"});
        x += r * 2;
        y += r * 2;
      });
      //return [{r:"250", x:"250", y:"250", fill:"#5EAFC6", stroke:"grey"}]
      return data;
    }
  }
};
</script>

<style>
</style>
