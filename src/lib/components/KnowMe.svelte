<script lang="ts">
  import content from "../../content/content.json";
  import developer from "../../content/developer.svg";

  function getIDFromName(name: string) {
    return `${name.toLowerCase().replaceAll(" ", "")}`;
  }
</script>

<section
  id={getIDFromName(content.headerLinks[0])}
  class="py-[6em] px-[3em] md:p-[7em] bg-[#face55] min-h-[100vh]"
>
  <div class="max-w-[1344px] mx-auto lg:grid grid-cols-12">
    <h2 class="text-2xl md:text-3xl font-semibold leading-[1.2] mb-[16px] col-span-12">
      {content.knowMeSection.title}
    </h2>
    <aside class="text-lg lg:col-span-6">
      {@html content.knowMeSection.content}
    </aside>
    <aside class="lg:pl-[1em] xl:px-[3em] lg:col-span-6 relative">
      <img src={developer} alt={"developer"} title="Designed by Freepik" class="w-[100%]" />
      <a href="https://www.freepik.com" target="_blank" class="absolute top-[20%] lg:top-[10%] xl:top-[15%] left-[50%] text-xs ">Designed by Freepik</a>
    </aside>
  </div>
</section>
