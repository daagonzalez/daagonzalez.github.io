<script>
    import { scrollTo } from "svelte-scrolling";

    let menuOpen = false;

    const navItems = [
        { name: "Home", target: "home" },
        { name: "Projects", target: "projects" },
        { name: "Contact", target: "contact" },
    ];

    function toggleMenu() {
        menuOpen = !menuOpen;
    }
</script>

<nav class="bg-red-900/80 fixed top-0 w-full z-50 p-4">
    <div class="container mx-auto flex justify-between items-center">
        <button class="block md:hidden text-white" on:click={toggleMenu}>
            <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="2"
                stroke="currentColor"
                class="w-8 h-8"
            >
                <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M4 6h16M4 12h16M4 18h16"
                />
            </svg>
        </button>
        <ul class="hidden md:flex space-x-8">
            {#each navItems as item}
                <li class="my-0">
                    <!-- svelte-ignore a11y-missing-attribute -->
                    <a
                        class="text-white hover:text-black font-bold cursor-pointer no-underline"
                        use:scrollTo={item.target}
                    >
                        {item.name}
                    </a>
                </li>
            {/each}
        </ul>
        <ul
            class="absolute left-0 top-full w-full bg-red-900/90 flex flex-col items-center space-y-4 p-4 md:hidden transition-all duration-300"
            class:hidden={!menuOpen}
        >
            {#each navItems as item}
            <li class="my-0">
                <!-- svelte-ignore a11y-missing-attribute -->
                <!-- svelte-ignore a11y-click-events-have-key-events -->
                <!-- svelte-ignore a11y-no-static-element-interactions -->
                <a
                    class="text-white hover:text-black font-bold cursor-pointer no-underline"
                    use:scrollTo={item.target}
                    on:click={() => (menuOpen = false)}
                >
                    {item.name}
                </a>
            </li>
            {/each}
        </ul>
    </div>
</nav>
