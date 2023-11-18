<template>
    <div class="group">
        <div class="head">
            <header class="header">
            <h1 class="logo">LOGO</h1>
            <div class="icon-items">
                <div class="icon-item">
                    <img class="icon" src="../assets/icon-acc.png" alt="Account icon">
                    <span>Account</span>
                </div>
                <div class="icon-item">
                    <img class="icon" src="../assets/icon-wishlist.png" alt="Wishlist icon">
                    <span>Wishlist</span>
                </div>
                <div class="icon-item">
                    <img class="icon" src="../assets/icon-cart.png" alt="Cart icon">
                    <span>Cart</span>
                </div>
            </div>
        </header>
        </div>
        <div class="rectangle">
            <div class="category-frame">
                <p>Grocery</p>
                <p>Electronics</p>
                <p>Pets</p>
                <p>Stationary</p>
                <p>Personal Care</p>
                <p>Toys & Video games</p>
                <p>Furniture</p>
                <p>Baby</p>
                <p>Beauty</p>
                <p>Clothing</p>
                <p>Sports</p>
                <p>Brand</p>
            </div>
        </div>
        <div class="breadcrumb">
            <div class="bread-crumb">
                <div class="page-menu">
                    <p class="page-text">Home</p>
                </div>
                <div class="separator">
                    <p>/</p>
                </div>
                <div class="page-menu">
                    <p class="page-text">Furniture</p>
                </div>
                <div class="separator">
                    <p>/</p>
                </div>
                <div class="page-menu">
                    <p class="page-text-last">Furniture</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        
    }
</script>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Lato&display=swap');

.group {
    width: 1440px;
    height: 155px;
    flex-shrink: 0;
}

.head {
    width: 1440px;
    height: 45px;
    flex-shrink: 0;
}
.header {
    width: 1440px;
    height: 70px;
    flex-shrink: 0;
}

.logo {
    display: inline-flex;
    color: var(--Text-Color, #1B1C1E);
    font-family: Lato;
    font-size: 25px;
    font-style: normal;
    font-weight: 700;
    line-height: 30px; /* 120% */
}

.icon-items {
    display: inline-flex;
    align-items: flex-start;
    gap: 22px;
    margin-left: 950px;
}

.icon-item {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 4px;
}
.icon {
    width: 17.273px;
    height: 20px;
    flex-shrink: 0;
}

span {
    color: #000;

    /* Display 2 */
    font-family: Lato;
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
}

.rectangle {
    width: 1440px;
    height: 45px;
    flex-shrink: 0;
    background: var(--Button-Text, #FBFBFB);
}

.category-frame {
    display: inline-flex;
    justify-content: center;
    align-items: center;
    gap: 40px;
}

.category-frame p {
    color: #000;

    /* Display 1 */
    font-family: Lato;
    font-size: 14px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
}

.breadcrumb {
    width: 1440px;
    height: 40px;
    flex-shrink: 0;
}

.bread-crumb{
    display: inline-flex;
    align-items: center;
}

.page-menu {
    display: flex;
    padding: 3.599px 7.197px;
    justify-content: center;
    align-items: center;
    gap: 6px;
}

.separator {
    display: flex;
    width: 8px;
    padding: 3.599px 7.197px;
    flex-direction: column;
    align-items: center;
    gap: 8.997px;
}

.page-text {
    color: var(--Text-Color, #1B1C1E);

    /* H5 */
    font-family: Lato;
    font-size: 13px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
}

.page-text-last {
    color: var(--Shapes, #C1C1C1);

    /* H5 */
    font-family: Lato;
    font-size: 13px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
}
</style>

