<script lang="ts">
	import '../app.css';
	let isMenuOpen = false;
</script>

<style>
    /* Navbar styling */
    .navbar {
        background-color: #dc173a;
        padding: 1.5rem 2.5rem;
        display: flex;
        align-items: center;
        justify-content: space-between;
        position: relative;
        z-index: 10;
    }

    .brand {
        color: white;
        font-size: 1.5rem;
        font-weight: bold;
    }

    .hamburger {
        display: none;
        flex-direction: column;
        gap: 4px;
        cursor: pointer;
    }

    .hamburger div {
        width: 24px;
        height: 3px;
        background-color: white;
        transition: 0.3s;
    }

    .menu {
        display: flex;
        gap: 2rem;
    }

    .menu-item {
        color: white;
        text-decoration: none;
        font-size: 1rem;
        transition: color 0.3s;
    }

    .menu-item:hover {
        color: #CCCCCC;
    }

    /* Responsive styles */
    @media (max-width: 768px) {
        .menu {
            display: none;
            flex-direction: column;
            gap: 1rem;
            position: absolute;
            top: 100%;
            left: 0;
            width: 100%;
            background-color: #D20F32;
            padding: 1.5rem;
            box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        .menu.open {
            display: flex;
            gap: 2rem;
        }

        /* Additional spacing to avoid overlap */
        .content {
            margin-top: 0; /* Default margin when menu is closed */
            transition: margin-top 0.3s ease;
        }

        /* Increase margin when menu is open */
        .content.menu-open {
            margin-top: 200px; /* Adjust based on menu height */
        }

        .hamburger {
            display: flex;
        }
    }
</style>

<div class="navbar">
    <div class="brand">
        <a href="./">ResQ</a>
    </div>

    <!-- Hamburger Icon -->
    <button 
        class="hamburger" 
        on:click={() => (isMenuOpen = !isMenuOpen)} 
        on:keydown={(e) => e.key === 'Enter' && (isMenuOpen = !isMenuOpen)}
        aria-expanded={isMenuOpen}
        aria-label="Toggle menu">
        
        <div></div>
        <div></div>
        <div></div>
    </button>

    <!-- Navigation Menu -->
    <div class={`menu ${isMenuOpen ? 'open' : ''}`}>
        <a href="request" class="menu-item">Emergency</a>
        <a href="hotlines" class="menu-item">Hotlines</a>
        <a href="contact" class="menu-item">Contact</a>
    </div>
</div>

<!-- Slot for page content -->
<div class={`content ${isMenuOpen ? 'menu-open' : ''}`}>
    <slot />
</div>
