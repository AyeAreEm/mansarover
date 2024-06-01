<script lang="ts">
import setlunch from "/src/public/mansarover_setlunch.jpg";
import norm_menu from "/src/public/mansarover_menu.jpg";
import halal_logo from "/src/public/halal_logo.png";

let enlarge_dialog: HTMLElement;
let enlarge_src: string;

let contact_dialog: HTMLElement;

function toggle_enlarge_menu(this: HTMLElement) {
    enlarge_src = this.getAttribute("src") || "";
    enlarge_dialog.showModal();
}

function enlarge_close(event: Event) {
    if (event.target === enlarge_dialog) {
        enlarge_dialog.close();
    }
}

function contact_close(event: Event) {
    if (event.target === contact_dialog) {
        contact_dialog.close();
    }
}
</script>

<main>
<div class="top_header">
    <button style="float: left;"><h1>Mansarover</h1></button>
    <button on:click={contact_dialog.showModal()} style="float: right;" class="contact"><h1>Contact</h1></button>
</div>
<img class="halal_logo" src={halal_logo} alt="mansarover logo">

<div class="menus">
    <h1>Menus</h1>
    <img on:click={toggle_enlarge_menu} src={setlunch} alt="mansarover setlunch">
    <img on:click={toggle_enlarge_menu} src={norm_menu} alt="mansarover menu">
</div>

<dialog bind:this={enlarge_dialog} on:click={enlarge_close} id="enlarge_dialog">
    <img src="{enlarge_src}" alt="menu">
</dialog>

<dialog bind:this={contact_dialog} on:click={contact_close} id="contact_dialog">
    <h1>Local number: 2109 1927</h1>
    <h1>WhatsApp: 6224 9937</h1>
</dialog>
</main>

<style>
.top_header {
    background: rgb(168,32,55);
    height: 5vh;
}

.top_header h1 {
    font-size: 2rem;
}

.top_header button {
    border: none;
    background: none;
    margin: 0;
    padding: 0;
    color: white;
}

.halal_logo {
    position: fixed;
    right: 0;
    min-width: 100px;
    width: 7%;
}

.menus {
    margin-top: 5%;
    width: 100%;
}

.menus img {
    float: left;
    width: 40%;
    height: 70vh;
    margin-left: 5%;
    margin-right: 5%;
}

.menus img:hover {
    cursor: pointer;
}

.contact:hover {
    cursor: pointer;
}

#enlarge_dialog {
    margin: auto;
    height: 100vh;
    width: 80vw;
    padding: 0.5rem;
    border-radius: 0.5em;
    z-index: 10;
}

#contact_dialog {
    margin: auto;
}

dialog[open] {
    animation: fade-in 150ms cubic-bezier(0, 0, 0.2, 1);
}

@media (max-width: 600px) {
    .menus img {
        float: none;
        width: 80%;
        margin-left: 5%;
        margin-right: 5%;
    }
}
</style>
