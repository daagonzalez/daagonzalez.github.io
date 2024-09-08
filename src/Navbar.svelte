<script>
    import {scrollTo} from 'svelte-scrolling';
</script>
<nav>
    <ul>
        <li>
            <!-- svelte-ignore a11y-missing-attribute -->
            <a use:scrollTo={'home'}> Home </a>
        </li>
        <li>
            <!-- svelte-ignore a11y-missing-attribute -->
            <a use:scrollTo={'projects'}> Projects </a>
        </li>
        <li>
            <!-- svelte-ignore a11y-missing-attribute -->
            <a use:scrollTo={'contact'}> Contact </a>
        </li>
    </ul>
</nav>

<style>
    nav ul {
        list-style: none;
        display: flex;
        justify-content: center;
        position: fixed;
        top: 0;
        width: 100%;
        background-color: rgba(117, 55, 66, 0.8);
        padding: 10px;
        margin: 0;
        z-index: 1000;
    }

    nav ul li {
        margin: 0 15px;
    }

    nav ul li a {
        text-decoration: none;
        color: #fff;
        font-weight: bold;
        cursor: pointer;
    }

    nav ul li a:hover {
        color: #dfdddd;
    }
</style>
