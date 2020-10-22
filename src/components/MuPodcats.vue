<template>
  <div class="podcast" @click="$emit('click')">
    <img class="podcast_image" :src="image" :alt="name" />
    <p class="podcast_name">{{ name }}</p>
    <p class="podcast_album">{{ album }}</p>
  </div>
</template>

<script>
export default {
  name: "MuPodcast",

  props: {
    image: {
      type: String,
      required: true,
    },
    album: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
  },
};
</script>

<style  scoped>
.podcast {
  width: 140px;
  text-align: center;
  cursor: pointer;
}

.podcast_active {
  border: 5px solid #2196F3;
}

.podcast_image {
  width: 160px;
  height: 160px;
  object-fit: cover;
  margin-right: 50px;
}
.podcast_name {
  margin: 0;
  margin-top: 4px;
  font-weight: bold;
  font-size: 14px;
}
.podcast_album {
  font-weight: 500;
  font-family: Quicksand;
  font-size: 12px;
  margin-left: 0px;
}
</style>