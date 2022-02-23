<script lang="ts">
  import CatCard from "./lib/CatCard.svelte";
  import UserCard from "./lib/UserCard.svelte";
  import data from "./assets/data.json";
  import avatar from "./assets/image-jeremy.png";

  interface User {
    name: string;
    avatar_URL: string;
  }

  let user: User = {
    name: "Jeremy Robson",
    avatar_URL: avatar,
  };
  console.log(user);
</script>

<main>
  <UserCard {user} />
  <div class="cards">
    {#each data as user}
      <CatCard data={user} />
    {/each}
  </div>
</main>

<style>
  main {
    display: flex;
  }
  .cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 1rem;
    width: 66%;
  }
</style>
