<script>
  import Header from "../components/Header.svelte";
  import Main from "../components/Main.svelte";
  import Sidebar from "../components/Sidebar.svelte";
  import TimeLine from "../components/TimeLine.svelte";
  import { onMount } from "svelte";
  import posts from "../../public/api/posts.json";
  require.context("../../public/images", false, /\.(jpg|png|gif|jpeg)$/);

  let data = {};
  const API = posts;

  onMount(async () => {
    const response = await fetch(API);
    data = await response.json();
  });
</script>

<Header />
<Main>
  <TimeLine posts={data.posts} />
  <Sidebar {...data.user} />
</Main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Lato:wght@300;400&display=swap");
  @import url("https://fonts.googleapis.com/css2?family=Pacifico&display=swap");

  :global(body) {
    background-color: #fafafa;
    color: rgba(38, 38, 38, 0.7);
    font-family: "Lato", sans-serif;
    margin: 0;
    padding: 0;
  }
  :global(h1, h2, h3) {
    margin: 0;
    padding: 0;
  }
</style>
