<script>
    import { createClient } from "@supabase/supabase-js";

    const supbaseUrl = import.meta.env.PUBLIC_SUPABASE_URL;
    const supabaseAnonKey = import.meta.env.PUBLIC_SUPABASE_ANON_KEY;

    const supabase = createClient(supbaseUrl, supabaseAnonKey);

    let email = "";
    let loading = false;
    let message = "";
    let messageType = "";

    async function handleSubmit() {
        if (!email) {
            message = "Veuillez entre une adresse email.";
            messageType = "error";
            return;
        }

        loading = true;
        message = "";

        const { error } = await supabase
            .from("Email")
            .insert([{ email: email }]);

        if (error) {
            message = `Erreur = ${error.message}`;
            messageType = "error";
            console.error("Erreur Supabase:", error);
        } else {
            message: "Merci ! Votre email à bien été enregistré.";
            messageType = "success";
            email = "";
        }

        loading = false;
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input
        type="email"
        bind:value={email}
        placeholder="Votre adresse email"
        disabled={loading}
    />
    <button type="submit" class="button button-primary" disabled={loading}>
        {#if loading}
            Envoie en cours...
        {:else}
            Rejoindre
        {/if}
    </button>
</form>

{#if message}
    <p class="message {messageType}">{message}</p>
{/if}

<style>
    form {
        display: flex;
        gap: 0.5rem;
        align-items: center; /* Aligne verticalement au centre */
        justify-content: center;
        flex-direction: column;
        margin-top: 2rem;
    }

    input,
    button {
        font-size: 1rem; /* Même taille de police */
        padding: 0.75rem 1.5rem; /* Même padding vertical et horizontal */
        border-radius: 9999px;
        box-sizing: border-box; /* Très important pour un calcul de taille cohérent */
    }

    input {
        border: 1px solid #ccc;
        min-width: 250px;
    }

    /* On s'assure que le bouton a une bordure de la même taille, mais transparente */
    button {
        border: 1px solid transparent;
    }

    .message {
        margin-top: 1rem;
        text-align: center;
        font-weight: 500;
    }
    .success {
        color: green;
    }
    .error {
        color: red;
    }
</style>
