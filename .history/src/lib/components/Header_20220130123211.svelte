<script lang="ts">
  import MainNav from "$lib/components/MainNav.svelte";
  import LogoSVG from "$lib/components/LogoSVG.svelte";
  import DarkModeToggle from "$lib/components/DarkModeToggle.svelte";
  import { isMenuOpen, isScrollingDown } from "$lib/data/store";
  import HamburgerMenuButton from "$lib/components/HamburgerMenuButton.svelte";

  const toggleMenu = (): void => {
    isMenuOpen.set(!$isMenuOpen);
  };

  const handleClick = (): void => {
    if ($isMenuOpen) toggleMenu();
  };

  // I don't love any part of this, but it's necessary to make the "skip to main content" link work properly, so we'll live with it.
  const focusMain = (e: Event): void => {
    e.preventDefault();
    const main = document.querySelector("main");
    main.focus();
  };
</script>

<div>
  <header class="header">
    <a
      on:click|preventDefault={focusMain}
      class="skip-to-content-link"
      href="#main"
    >
      Skip to main content
    </a>

    <a href="/" class="logo" on:click={handleClick}>
      <LogoSVG />
    </a>

    <div
      class="icon-container"
      class:sticky={$isMenuOpen}
      class:ghosty={$isScrollingDown && !$isMenuOpen}
    >
      <DarkModeToggle />
      <HamburgerMenuButton closeOnly={false} />
      <MainNav />
    </div>
    <svg
      class="background--custom"
      id="demo"
      viewBox="0 0 100 100"
      preserveAspectRatio="none"
    >
      <path
        fill="#d56d3b"
        fill-opacity="0.5"
        d="M-100 -100L200 -100L200 50L-100 50Z"
        style="animation: path0 25s linear infinite alternate;"
      /><path
        fill="#ccff00"
        fill-opacity="0.8"
        d="M-100 -100L200 -100L200 50L-100 50Z"
        style="animation: path1 3.1055900621118013s linear infinite alternate;"
      /><path
        fill="#6efeb0"
        fill-opacity="0.4"
        d="M-100 -100L200 -100L200 50L-100 50Z"
        style="animation: path2 19.23076923076923s linear infinite alternate;"
      />
    </svg>
  </header>

  <noscript>
    <style>
      #dark-mode-toggle,
      #motion-toggle,
      #contact-form {
        display: none;
      }

      .page-head .heading-wrapper .brace.closing-brace {
        transform: translateX(0);
      }
    </style>
  </noscript>
</div>

<style lang="scss">
  @import "../assets/scss/vars";

  .icon-container {
    display: flex;
    align-items: center;
    position: fixed;
    right: 1rem;
    top: calc(1rem - 2px);
    transition: opacity 0.2s;

    @media (min-width: $xs) {
      position: static;
    }
  }

  .sticky {
    --ink: var(--white);
    --buttonBackground: transparent;
  }

  .logo {
    width: auto;
    height: 6.6rem;
    display: block;

    @media (min-width: $xxl) and (min-height: $md) {
      height: 3rem;
    }
  }

  .icon-container {
    display: flex;
    align-items: center;
    position: fixed;
    right: 1rem;
    top: calc(1rem - 2px);
    transition: opacity 0.2s;

    @media (min-width: $xs) {
      position: static;
    }
  }

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    position: relative;
    padding: var(--quarterNote) var(--margin) var(--halfNote);

    @media (min-width: $xs) {
      padding: var(--halfNote) var(--margin);
    }
  }

  .skip-to-content-link {
    --itemTransition: 0.15s cubic-bezier(0.86, 0, 0.07, 1);

    transition: transform var(--itemTransition), opacity var(--itemTransition);
    position: absolute;
    top: -6rem;
    left: 1rem;
    padding: 0.5em;
    opacity: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 3rem;
    background: var(--darkBlue);
    color: var(--white);
    font-family: var(--headingFont);

    &:focus {
      transform: translateY(7rem);
      opacity: 1;
      z-index: 11;
    }
  }
</style>
