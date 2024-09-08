<nav>
    <ul>
        <li>
            <a href="#home"> Home </a>
        </li>
        <li>
            <a href="#projects"> Projects </a>
        </li>
        <li>
            <a href="#contact"> Contact </a>
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
        background: rgba(255, 255, 255, 0.8);
        padding: 10px;
        margin: 0;
        z-index: 1000;
    }

    nav ul li {
        margin: 0 15px;
    }

    nav ul li a {
        text-decoration: none;
        color: #333;
        font-weight: bold;
        cursor: pointer;
    }

    nav ul li a:hover {
        color: #007bff;
    }
</style>
