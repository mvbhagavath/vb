<script>
  import GetInTouch from "../lib/components/GetInTouch.svelte";
  import Hero from "../lib/components/Hero.svelte";
  import KnowMe from "../lib/components/KnowMe.svelte";
  import MyWork from "../lib/components/MyWork.svelte";
  import content from "../content/content.json";
</script>

<svelte:head>
  <title>{content.name}</title>
  <meta name="description" content={content.description} />
</svelte:head>

<div class="scroll-smooth overflow-y-scroll font-roboto">
  <Hero />
  <KnowMe />
  <MyWork />
  <GetInTouch />
</div>
