<script>
  import { fade } from "svelte/transition";
  import { createEventDispatcher } from "svelte";

  import PrimaryButton from "../../../Components/PrimaryButton.svelte";
  import SecondaryButton from "../../../Components/SecondaryButton.svelte";
  import Badge from "../../../Components/Badge.svelte";

  export let created,
    duration,
    id,
    name,
    date_in_series_pattern,
    status,
    time,
    local_date,
    local_time,
    yes_rsvp_count,
    link,
    description;

  const dispatch = createEventDispatcher();

  function showMore() {
    console.log(id);
    dispatch("toggleModal", id);
  }
</script>

<style>
  article {
    min-height: fit-content;
    display: flex;
    width: 100%;
    background-color: white;
    border: 0 solid #cfbcf2;
    border-radius: 5px;
    overflow: hidden;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
      0 2px 4px -1px rgba(0, 0, 0, 0.06);
    transition: all 0.35s;
  }

  article:hover {
    box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
  }

  .content {
    padding: 1rem;
    display: flex;
    flex-direction: column;
  }

  .content h1 {
    margin-bottom: 0;
    margin-top: 0;
  }

  .content h2 {
    margin-top: 0;
    margin-bottom: 20px;
    font-weight: lighter;
    font-size: 1rem;
    color: #3e4c59;
  }

  .content footer {
    margin-top: auto;
  }

  a {
    color: #62b0e8;
  }

  a:hover {
    color: #4098d7;
  }
</style>

<article transition:fade data-id={id}>
  <div class="content">
    <h1> {name} </h1>
    <h2>{local_date}, {local_time}</h2>
    <a href={link}> {link} </a>
    <footer>
      <PrimaryButton on:click={showMore} content="See Details" />
      <SecondaryButton content={'Attend'} />
    </footer>
  </div>
</article>
