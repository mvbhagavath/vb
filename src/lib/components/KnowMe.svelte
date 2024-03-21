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
  <div class="max-w-[1344px] mx-auto xl:grid grid-cols-12">
    <h2 class="text-3xl font-semibold leading-2 mb-[16px] col-span-12">
      {content.knowMeSection.title}
    </h2>
    <aside class="text-lg xl:col-span-6">
      {@html content.knowMeSection.content}
    </aside>
    <aside class="px-[3em] xl:col-span-6 relative">
      <img src={developer} alt={"developer"} title="Designed by Freepik" class="w-[100%]" />
      <a href="https://www.freepik.com" target="_blank" class="absolute top-[20%] left-[50%] text-xs ">Designed by Freepik</a>
    </aside>
  </div>
</section>
