<template>
    <li>
        <h2>
            <a href="artist.url">{{ artist.name }}</a>
        </h2>
        <img :src="artist.image[2]['#text']" alt="">
    </li>
</template>

<script>

export default {
  name: 'artist',
  props:['artist']
}

</script>
