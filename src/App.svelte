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
  <div class="user"><UserCard {user} /></div>

  <div class="cards">
    {#each data as user}
      <CatCard data={user} />
    {/each}
  </div>
</main>

<style>
  @media (min-width: 1100px) {
    main {
      display: flex;
      width: 1100px;
    }
    .user {
      width: 25%;
      margin-right: 1rem;
    }
    .cards {
      width: 75%;
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      grid-template-rows: 1fr 1fr;
      grid-gap: 1.5rem;
    }
  }
  @media (max-width: 1100px) {
    main {
      width: 400px;
      margin: 0 auto;
      padding: 1rem;
    }
    .user {
      margin-bottom: 2rem;
    }
    .cards {
    }
  }
</style>
