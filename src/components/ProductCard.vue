<template>
  <div class="product-card">
    <div class="mask-group">
      <div class="bg-light">
        <img src="../assets/product.png" alt="Product">
      </div>
    </div>
    <div class="fav">
      <div class="rec"></div>
      <img src="../assets/Favorite.png" alt="Favorite" class="fav-icon">
    </div>
    <div class="context">
      <div class="product-details">
        <p>Lorem ipsum dolor sit amet consectetur</p>
        <p>150$</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  
}
</script>

<style scoped>
.product-card {
  position: relative;
  width: 100%;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
}

.mask-group {
  position: relative;
  overflow: hidden;
  width: 100%;
  padding-top: 100%; /* Maintain aspect ratio for the image container */
}

.bg-light {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #F5F5F5; /* Light background color for the image container */
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover; /* Maintain aspect ratio for the image */
}

.fav {
  position: absolute;
  top: 10px;
  right: 10px;
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
}

.rec {
    position: absolute;
    top: -5px;
    right: -5px;
    width: 36.16px;
    height: 37.733px;
    flex-shrink: 0;
    border-radius: 62.888px;
    background: var(--White, #FFF);
    margin-left: 4px;
}

.fav-icon {
    position: absolute;
    top: 3px;
    right: 2px;
    width: 23.583px;
    height: 20.635px;
    flex-shrink: 0;
    z-index: 1;
}

.context {
    display: inline-flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 5px;
}

.product-details {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 3px;
}

.product-details p:first-child{
    width: 248.406px;
    color: var(--Text-Color, #1B1C1E);

    /* Display 3 */
    font-family: Lato;
    font-size: 18px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
}

.product-details p:last-child {
    width: 44.021px;
    color: var(--Text-Color, #1B1C1E);

    /* Button Text */
    font-family: Lato;
    font-size: 18px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
}
</style>
