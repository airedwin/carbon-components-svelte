<script>
  /** Specify the number of accordion items to render */
  export let count = 4;

  /**
   * Specify alignment of accordion item chevron icon
   * @type {"start" | "end"}
   */
  export let align = "end";

  /**
   * Specify the size of the accordion
   * @type {"sm" | "xl"}
   */
  export let size = undefined;

  /** Set to `false` to close the first accordion item */
  export let open = true;

  import ChevronRight16 from "carbon-icons-svelte/lib/ChevronRight16/ChevronRight16.svelte";
  import SkeletonText from "../SkeletonText/SkeletonText.svelte";
</script>

<!-- svelte-ignore a11y-mouse-events-have-key-events -->
<ul
  class:bx--skeleton="{true}"
  class:bx--accordion="{true}"
  class:bx--accordion--start="{align === 'start'}"
  class:bx--accordion--end="{align === 'end'}"
  class:bx--accordion--sm="{size === 'sm'}"
  class:bx--accordion--xl="{size === 'xl'}"
  {...$$restProps}
  on:click
  on:mouseover
  on:mouseenter
  on:mouseleave
>
  {#if open}
    <li
      class:bx--accordion__item="{true}"
      class:bx--accordion__item--active="{true}"
    >
      <span class:bx--accordion__heading="{true}">
        <ChevronRight16 class="bx--accordion__arrow" />
        <SkeletonText class="bx--accordion__title" />
      </span>
      <div class="bx--accordion__content">
        <SkeletonText width="90%" />
        <SkeletonText width="80%" />
        <SkeletonText width="95%" />
      </div>
    </li>
  {/if}
  {#each Array.from({ length: open ? count - 1 : count }, (_, i) => i) as item (item)}
    <li class="bx--accordion__item">
      <span class="bx--accordion__heading">
        <ChevronRight16 class="bx--accordion__arrow" />
        <SkeletonText class="bx--accordion__title" />
      </span>
    </li>
  {/each}
</ul>
