<script>
  import "./App.scss";
  import "./reset.scss";
  let names = "";
  $: pages = names.split(",").reduce((resultArray, item, index) => {
    const chunkIndex = Math.floor(index / 4);

    if (!resultArray[chunkIndex]) {
      resultArray[chunkIndex] = []; // start a new chunk
    }

    resultArray[chunkIndex].push({
      name: item
    });

    return resultArray;
  }, []);
</script>

<style>

</style>

<main>
  <form class="form">
    <input
      bind:value={names}
      placeholder="enter your names"
      className="form__names" />
  </form>
  <div>
    {#each pages as page}
      <div class="page page__recto">
        {#each page as { name }}
          <article class="bookmark bookmark__recto">
            <section class="bookmark__face bookmark__face--recto">
              <h3 class="bookmark__face-text">{name}</h3>
            </section>
            <section class="bookmark__face bookmark__face--verso" />
          </article>
        {/each}
      </div>
      <div class="page page__verso">
        {#each page as { name }}
          <article class="bookmark bookmark__verso">
            <section class="bookmark__face bookmark__face--verso" />
          </article>
        {/each}
      </div>
    {/each}

  </div>
</main>
