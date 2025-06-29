<script>
    import { isMenuOpen } from "../stores/MenueStore";

    function toggleMenu() {
        $isMenuOpen = !$isMenuOpen
        
    }
</script>

<header>
    <a href="/" class="logo">
        <strong>DL</strong>
        <span>DEALINK</span>
    </a>
    <nav class="desktop-nav">
        <ul>
            <li><a href="#">Accueil</a></li>
            <li><a href="#">Tarif</a></li>
            <li><a href="#">Mission</a></li>
            <li><a href="#">Profil</a></li>
            <li><a href="#" class="button button-secondary">Inscription</a></li>
        </ul>
    </nav>

    <button class="hamburger" on:click={toggleMenu} aria-label="Menu">
        <div class="bar"></div>
        <div class="bar"></div>
        <div class="bar"></div>
    </button>

    {#if $isMenuOpen}
        <nav class="mobile-nav">
            <ul>
                <li><a href="#">Accueil</a></li>
                <li><a href="#">Tarif</a></li>
                <li><a href="#">Mission</a></li>
                <li><a href="#">Profil</a></li>
                <li>
                    <a href="#" class="button button-secondary">Inscription</a>
                </li>
            </ul>
        </nav>
    {/if}
</header>

<style>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        max-width: 1440px;
        padding: 1.5rem 5%;
        margin: 0 auto;
        box-sizing: border-box;
        position: relative;
    }
    .logo {
        font-weight: bold;
        font-size: 1.5rem;
        text-decoration: none;
        color: black;
    }
    .logo span {
        font-weight: normal;
        margin-left: 0.5rem;
    }
    nav ul {
        display: flex;
        align-items: center;
        list-style: none;
        margin: 0;
        padding: 0;
        gap: 2rem;
    }
    nav a:not(.button) {
        text-decoration: none;
        color: #555;
        font-size: 1rem;
    }

    .hamburger {
        display: none;
        flex-direction: column;
        justify-content: space-around;
        width: 2rem;
        height: 2rem;
        background: transparent;
        border: none;
        cursor: pointer;
        padding: 0;
        z-index: 10;
    }

    .hamburger .bar {
        width: 2rem;
        height: 0.25rem;
        background-color: #333;
        border-radius: 10px;
        transition: all 0.3s linear;
    }

    .mobile-nav {
        position: absolute;
        top: 5rem;
        left: 0;
        width: 100svw;
        background-color: white;
        box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
        padding-top: 5rem;
        flex-direction: column;
        box-sizing: border-box;
    }
    .mobile-nav ul {
        flex-direction: column;
        width: 100%;
        padding-bottom: 1rem;
    }

    .mobile-nav li {
        text-align: center;
        width: 100%;
        font-size: 2rem;
        font-weight: 700;
        padding: 1rem 0;
    }

    .mobile-nav .button {
        width: 100%; /* Le bouton prend 100% de la largeur du <li> */
        display: block; /* On s'assure qu'il remplit l'espace */
        box-sizing: border-box; /* Pour que le padding/bordure ne le fasse pas déborder */
        margin: 0; /* On supprime la marge du bouton lui-même */
    }

    @media (max-width: 768px) {
        .desktop-nav {
            display: none;
        }

        .hamburger {
            display: flex;
        }

        .mobile-nav {
            display: flex;
        }
    }
</style>
