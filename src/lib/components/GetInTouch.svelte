<script lang="ts">
  import content from "../../content/content.json";
  import instagram from "../images/instagram.svg";
  import github from "../images/github.svg";
  import linkedin from "../images/linkedin.svg";
  import facebook from "../images/facebook.svg";
  import x from "../images/x.svg";

  const getIDFromName = (name: string) => {
    return `${name.toLowerCase().replaceAll(" ", "")}`;
  };

  const getSocialWidget = (name: string, link: string, icon?: string) => {
    return `<a href=${link} target="_blank" class="w-[50px] h-[50px]">
      <img src=${icon} alt="${name}" title="${name}"/>
      </a>`;
  };
</script>

<section
  id={getIDFromName(content.headerLinks[2])}
  class="py-[4em] px-[2em] md:p-[7em] bg-[#face55]"
>
  <div class="max-w-[1344px] mx-auto">
    <h2 class="text-3xl font-semibold leading-5 mb-[16px] col-span-12">
      {content.getInTouchSection.title}
    </h2>
    <article class="text-lg">
      {content.getInTouchSection.description}
    </article>
    <div class="mb-[32px] text-lg">
      {#if content.getInTouchSection.email !== ""}
        <span>Drop a mail @ </span><a
          class="hover:underline"
          href={`mailto:${content.getInTouchSection.email}`}
          >{content.getInTouchSection.email}</a
        >
      {/if}
      {#if content.getInTouchSection.phone !== ""}
        <span>Phone:</span><a href={`tel:${content.getInTouchSection.phone}`}
          >{content.getInTouchSection.phone}</a
        >
      {/if}
    </div>
    <ul class="flex justify-center md:justify-start">
      {#if content.getInTouchSection.socials.gitHub !== ""} 
      <li class="mr-[8px] w-[40px]">
        {@html getSocialWidget(
          "github",
          content.getInTouchSection.socials.gitHub,
          github
        )}
      </li>
      {/if}
      {#if content.getInTouchSection.socials.linkedIn !== ""} 
      <li class="mr-[8px]">
        {@html getSocialWidget(
          "linkedIn",
          content.getInTouchSection.socials.linkedIn,
          linkedin
        )}
      </li>
      {/if}
      {#if content.getInTouchSection.socials.instagram !== ""} 
        <li class="mr-[8px]">
          {@html getSocialWidget(
            "instagram",
            content.getInTouchSection.socials.instagram,
            instagram
          )}
        </li>
      {/if}
      {#if content.getInTouchSection.socials.facebook !== ""} 
      <li class="mr-[8px]">
        {@html getSocialWidget(
          "facebook",
          content.getInTouchSection.socials.facebook,
          facebook
        )}
      </li>
      {/if}
      {#if content.getInTouchSection.socials.x !== ""} 
      <li class="mr-[8px]">
        {@html getSocialWidget("x", content.getInTouchSection.socials.x, x)}
      </li>
      {/if}
    </ul>
  </div>
</section>
