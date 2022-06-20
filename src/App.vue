
<template>

  <div class="container mt-4">

    <div class="d-flex mt-3" v-for="post in posts">
      <div class="flex-shrink-0">
         <img :src="post.data.thumbnail" alt="kskksk" onerror="if (this.src != '') this.src = 'src/assets/download.png';" style="width:140px" /> 
      </div>
      <div class="flex-grow-1 ms-3">
      {{post.data.title}}
      <p>
        <span class="badge bg-danger">{{post.data.ups}}   ⬆ </span>
      
      </p>
      <p>
        <span class="badge bg-info">{{post.data.num_comments}} comments</span>
      
      </p></div>
    </div>
  </div>
</template>
<script>
 import image from './assets/download.png';
export default {
  data: () => ({
    posts: [],
  }),
  mounted() {
 
    fetch("https://www.reddit.com/r/ArsenalFC/.json")
      .then((response) => response.json())
      .then((data) => {
        this.posts = data.data.children;
      });
  },
  methods: {
    
  },
};
</script>
