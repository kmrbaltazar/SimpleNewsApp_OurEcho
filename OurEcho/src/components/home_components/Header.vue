<template>
    <header>
        <div class="logo_wrapper">
            <a href="">
                <img src="@/assets/images/ourecho_logo.png" alt="Our Echo logo">
            </a>
        </div>
        <a href="">
            <img src="@/assets/icons/menu-hamburger.svg" alt="Hamburger Icon">
        </a>
    </header>
</template>

<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #006297;
    padding: 0 20px;
    height: 70px;
}

.logo_wrapper {
    height: 55px;
}

@media (min-width: 63em) {
    header {
        width: 40%;
    }
}
</style>
