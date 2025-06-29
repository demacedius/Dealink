<script>
    let isPorteur = false; // false = Freelance, true = Porteur d'affaires

    $: mainVerb = isPorteur ? "Proposez" : "Trouvez";

</script>

<div class="hero-content">
    <h1>{mainVerb} des missions tech en un clic</h1>
    <p class="subtitle">
        La marketplace qui connecte les porteurs d'affaires et les freelances du
        numérique.
    </p>

    <div class="toggle-container">
        <span>Freelance</span>
        <label class="toggle-switch">
            <input type="checkbox" bind:checked={isPorteur} />
            <span class="slider"></span>
        </label>
        <span>Porteur d'affaires</span>
    </div>
</div>

<style>
    .hero-content {
        text-align: center;
        padding: 4rem 0;
    }

    h1 {
        font-size: 3.5rem;
        font-weight: 700;
        margin-bottom: 1rem;
    }

    .subtitle {
        font-size: 1.25rem;
        color: #555;
        margin-bottom: 3rem;
    }

    .toggle-container {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 1rem;
        font-weight: 500;
    }

    .toggle-switch {
        position: relative;
        display: inline-block;
        width: 60px;
        height: 34px;
    }

    .toggle-switch input {
        opacity: 0;
        width: 0;
        height: 0;
    }

    .slider {
        position: absolute;
        cursor: pointer;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background-color: #ccc;
        transition: 0.4s;
        border-radius: 34px;
    }

    .slider:before {
        position: absolute;
        content: "";
        height: 26px;
        width: 26px;
        left: 4px;
        bottom: 4px;
        background-color: white;
        transition: 0.4s;
        border-radius: 50%;
    }

    input:checked + .slider {
        background-color: #8b5cf6; /* Violet */
    }

    input:checked + .slider:before {
        transform: translateX(26px);
    }

    @media (max-width: 768px) {
        h1 {
            font-size: 2.5rem;
        }
    }
</style>
