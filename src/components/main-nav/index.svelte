<script lang="ts">
  import { goto } from "$app/navigation";
  import MobileMenu from "./mobile-menu/index.svelte";
  import MobileMenuToggle from "./mobile-menu/toggle.svelte";
  import NavItem from "./nav-item.svelte";
  import menuState from "./mobile-menu/state";
  import LoginButton from "./login-button.svelte";
  import Logo from "../svgs/logo.svelte";
  import { showHideOverflowY } from "../../utils/helper";

  const navItems = [
    {
      href: "/features",
      label: "Features",
    },
    {
      href: "/screencasts",
      label: "Screencasts",
      isHighlighted: true,
    },
    {
      href: "/blog",
      label: "Blog",
    },
    {
      href: "/docs",
      label: "Docs",
    },
    {
      href: "/changelog",
      label: "Changelog",
    },
    {
      href: "/pricing",
      label: "Pricing",
    },
  ];
</script>

<style type="text/postcss">
  nav {
    max-width: 1500px;
  }

  @media (min-width: 931px) {
    nav {
      @apply bg-sand-light;
    }

    .nav-items,
    .login-wrapper {
      @apply flex;
    }
  }
</style>

<nav
  id="choose-project-observer-target-top"
  class={`${$menuState ? "bg-off-white " : ""}mx-auto w-full`}
>
  <div class="flex items-center justify-between h-20 px-4 sm:px-8">
    <a
      on:contextmenu|preventDefault={() => goto("/media-kit")}
      href="/"
      aria-label="Gitpod"
      on:click={() => {
        $menuState = !menuState;
        showHideOverflowY(false);
      }}
    >
      <Logo />
    </a>
    <div class="nav-items hidden px-2 space-x-6 items-center md:space-x-12">
      {#each navItems as navItem}
        <NavItem {navItem} on:click={() => ($menuState = !$menuState)} />
      {/each}
    </div>
    <div class="login-wrapper hidden">
      <LoginButton />
    </div>
    <MobileMenuToggle />
  </div>
  <MobileMenu {navItems} />
</nav>
