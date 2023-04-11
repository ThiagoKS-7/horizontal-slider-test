<template>
  <div class="flex  flex-col items-center text-center">
    <div class="absolute top-2 right-2">
      <ThemeSwitch/>
    </div>
    <h1 class="text-3xl font-bold underline mb-5"> Slider example</h1>
    <div class="scrolling-wrapper" id="scrolling-container">
      <div v-for="item in list" class="card">
        <h1 class="text-2xl">{{ item.title }}</h1>
        <span class="text-xl">{{ item.description }}</span>
      </div>
    </div>
    <div>
      <input type="range" min="0" max="100" v-model="range" @input="scrollSlider()">
      {{ range }}
    </div>

  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      range: 0,
      list: [
        {
          title: "Title 1",
          description: "Lorem ipsum dolor sit amet.",
        },
        {
          title: "Title 2" ,
          description: "Lorem ipsum dolor sit amet.",
        },
        {
          title: "Title 3",
          description: "Lorem ipsum dolor sit amet.",
        },
        {
          title: "Title 4",
          description: "Lorem ipsum dolor sit amet.",
        }
      ]
    }
  },
  methods: {
    scrollSlider() {
      console.log(this.range)
      let panel = document.getElementById("scrolling-container")
      let total = panel.scrollWidth - panel.offsetWidth;
      let percentage = total*(this.range/100);
      panel.scrollLeft = percentage;
      console.log(total);
    }
  }
}
</script>
<style>
.scrolling-wrapper {
  @apply flex flex-nowrap overflow-x-auto w-[90%] h-[80vh];
}
.card {
  @apply min-w-[120vw] px-5 bg-sky-800 rounded mr-1 ml-1;
}
</style>