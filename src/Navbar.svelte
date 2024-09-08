<script>
    import { scrollTo } from "svelte-scrolling";

    const navItems = [
        { name: "Home", target: "home" },
        { name: "Projects", target: "projects" },
        { name: "Contact", target: "contact" },
    ];
</script>

<nav>
    <ul
        class="list-none flex flex-col md:flex-row justify-center fixed top-0 w-full bg-red-900/80 p-2.5 m-0 z-50"
    >
        {#each navItems as item}
            <li class="mx-4 my-2 md:my-0">
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
</nav>
