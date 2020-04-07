<template>
  <Layout>

    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <g-image
      alt="Example image"
      src="~/favicon.png"
      width="135"
    />

    <h1>Hello, world!</h1>

    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur excepturi labore tempore expedita, et iste tenetur suscipit explicabo! Dolores, aperiam non officia eos quod asperiores
    </p>

    <h1> Manual Loaded</h1>

    <ul>
      <li>
        <g-link to="/blog-html/blog-post-one">Post One</g-link>
      </li>
      <li>
        <g-link to="/blog-html/blog-post-two">Post Two</g-link>
      </li>
      <li>
        <g-link to="/blog-html/blog-post-three">Post Three</g-link>
      </li>
    </ul>

    <h1> Automatic Loaded</h1>

    <ul>
      <li
        v-for="post in $page.posts.edges"
        :key="post.node.id"
      >
        <g-link :to="post.node.path">{{ post.node.title }}</g-link>
      </li>
    </ul>

    <h1>Reddit Posts</h1>
    <div class="cards-list">
      <div
        v-for="(RedditPost,key) in $page.RedditPosts.edges"
        :key="key"
        class="card 1"
      >
        <div class="card_image">
          <g-image :src="RedditPost.node.fields.thumbhnail"></g-image>
        </div>
        <div>
          <h3>
            <g-link :to="RedditPost.node.path">
              {{ RedditPost.node.title }}
            </g-link>
          </h3>
        </div>
      </div>
    </div>

    <p class="home-links">
      <a
        href="https://gridsome.org/docs/"
        target="_blank"
        rel="noopener"
      >Gridsome Docs</a>
      <a
        href="https://github.com/gridsome/gridsome"
        target="_blank"
        rel="noopener"
      >GitHub</a>
    </p>

  </Layout>
</template>

<page-query>
 query Posts {
  posts: allPost {
    edges {
      node {
        id
        title
        path

      }
    }
  }
  RedditPosts: allRedditPost{
  edges {
    node {
      title,
      path,
      fields{
        thumbhnail
      }

    }
  }
}
}

</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}

.cards-list {
  z-index: 0;
  width: 100%;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}

.card {
  padding: 5px;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  margin: 30px auto;
  width: 300px;
  height: 300px;
  border-radius: 40px;
  box-shadow: 5px 5px 30px 7px rgba(0, 0, 0, 0.25),
    -5px -5px 30px 7px rgba(0, 0, 0, 0.22);
  cursor: pointer;
  transition: 0.4s;
}

.card .card_image {
  width: inherit;
  height: inherit;
  border-radius: 40px;
}

.card .card_image img {
  width: inherit;
  height: inherit;
  border-radius: 40px;
  object-fit: cover;
}

.card .card_title {
  text-align: center;
  border-radius: 0px 0px 40px 40px;
  font-family: sans-serif;
  font-weight: bold;
  font-size: 30px;
  margin-top: -80px;
  height: 40px;
}

.card:hover {
  transform: scale(0.9, 0.9);
  box-shadow: 5px 5px 30px 15px rgba(0, 0, 0, 0.25),
    -5px -5px 30px 15px rgba(0, 0, 0, 0.22);
}

.title-white {
  color: white;
}

.title-black {
  color: black;
}

@media all and (max-width: 500px) {
  .card-list {
    /* On small screens, we are no longer using row direction but column */
    flex-direction: column;
  }
}

/*
.card {
  margin: 30px auto;
  width: 300px;
  height: 300px;
  border-radius: 40px;
  background-image: url('https://i.redd.it/b3esnz5ra34y.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  background-repeat: no-repeat;
box-shadow: 5px 5px 30px 7px rgba(0,0,0,0.25), -5px -5px 30px 7px rgba(0,0,0,0.22);
  transition: 0.4s;
}
*/
</style>
