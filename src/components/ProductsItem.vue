<template>
   
<!--TEMPLATE-->
  <li>
      <div class="product">
            <a href="" class="product__img">
              <img src="http://via.placeholder.com/150x150" alt="">
            </a>
            <div class="product__description">
                <div class="product__code">Код:{{Number(proditem.code)}}</div>
                <div class="product__title">{{proditem.title}}</div>
                <div class="product__tags"></div>
            </div>
            <div class="product__buy">
                <div class="product__price">
                    <span class="product__price-text">По карте<br>клуба</span>   
                    <span class="product__price-num">{{proditem.hasAlternateUnit ? proditem.priceGold : proditem.priceGoldAlt}} &#8381;</span>   
                </div>
                <div class="product__price">
                    <span class="product__price-num product__price-num_gray">{{proditem.hasAlternateUnit ? proditem.priceRetail : proditem.priceRetailAlt}} &#8381;</span>   
                </div>
                <div class="product__points">Можно купить за 231,75 балла</div>
                <div class="product__unit">
                    <div class="product__unit-select " v-bind:class="{'product__unit-select_active': proditem.hasAlternateUnit}" v-on:click='proditem.hasAlternateUnit= true' >За м. кв.</div>
                    <div class="product__unit-select" v-bind:class="{'product__unit-select_active': !proditem.hasAlternateUnit}" v-on:click='proditem.hasAlternateUnit= false'>За упаковку</div>
                </div>
                <div class="product__unit-info">
                    <span class="product__unit-info-inner">
                        Продается упаковками:<br>
                        1 {{proditem.unit}} = {{proditem.unitRatioAlt}} {{proditem.unitAlt}}
                    </span> 
                </div>
                <div class="btn__wrapper">
                    <div class="stepper">
                        <span class="stepper-arrow_up" v-on:click='proditem.unitRatio=Number(proditem.unitRatio) + 1'>+</span>
                        <span class="stepper-arrow_down" v-on:click='proditem.unitRatio<2? proditem.unitRatio=1: proditem.unitRatio=proditem.unitRatio-1 ' >-</span>
                        <input  class="product__count stepper-input" type="number" v-model="proditem.unitRatio">

                    </div>
                    <span class="btn btn_cart" v-bind:data-product-id="proditem.productId">
                        В корзину
                    </span>
                 </div>
            </div>
      </div>

  </li>
<!--TEMPLATE-->
    
</template>
<script>
export default {
    props:{
        proditem:{
            type:Object,
            required:true
        }
    },
    methods: {
    stepDown: function () {
    }
  }
}

 


</script>

<style lang="scss">

li{
list-style-type: none;
}
ul{
    padding: 0;
}
.product{
    display: flex;
    max-width: 750px;
    margin: 10px auto;
    border: 1px solid gray; 
    &__img{
        width: 150px;
        height: 150px;
        padding: 10px
    }
    &__description{
        padding: 10px;
        text-align: left;
    }
    &__code{
        font-size: 12px;
    }
    &__buy{
        width: 250px;
        padding: 10px;
    }
    &__price{
        display: flex;
        justify-content: flex-end;
        
    }
    &__price-text{
        font-size: 12px;
        margin-right: 5px;
    }
    &__price-num{
        font-size: 25px;
        font-weight: 400;
        line-height: 25px;
        color: #333;
        &_gray{
            color: #888;
        }
    }
    &__points{
        font-size: 12px;
        color: #888;
    }
    &__unit{
        margin: 5px 0;
        display: flex;
        justify-content: center;
    }
    &__unit-select{
        padding: 3px 5px ;
        font-size: 12px;
        cursor: pointer;
        &:hover{
            background: #aaa;
            transition: 0.3s;
        }
    }
    &__unit-select_active{
        color: #fff;
        background: #000;
        &:hover{
            background: #888;
        }
    }
    &__unit-info{
        border: 1px solid #888;
        padding: 5px;
        position: relative;
        &::before{
            content: '';
            position: absolute;
            width: 7px;
            height: 7px;
            border-right: 1px solid #888;
            border-bottom: 1px solid #888;
            bottom: -7px;
            transform: rotate(45deg);
            transform-origin: right;
            background: #fff;

        }
        
        &-inner{
        font-size: 14px;
        }
    }
    
    }
.stepper{
    position: relative;
    width: 48px;
    text-align: left;

    &-input {
    border: 1px solid #888;
    color: #333;
    font-size: 14px;
    margin: 0;
    width: 30px;
    height: 30px;
    text-align: center;
    }
    &-arrow_up{
       position: absolute;
       top: 0;
       right: 0;
       width: 15px;
       height: 16px;
       text-align: center;
       border: 1px solid #888;
       cursor: pointer;
       user-select: none;  
       &:hover{
           background: #aaa;
       }
    }
    &-arrow_down{
       position: absolute;
       bottom: 0;
       right: 0;
       width: 15px;
       height: 15px;
       text-align: center;
       border: 1px solid #888;
       cursor: pointer;
       user-select: none; 
       &:hover{
           background: #aaa;
       } 
   }
}
.btn__wrapper{
    display: flex;
    justify-content: center;
    width: 180px;
    margin: 10px 0;
}
.btn{
    line-height: 30px;
    color: #fff;
    background: #f90;
    padding: 0px 15px;
    margin-left: 5px;
    &:hover{
        background: #f65;
        transition: 0.3s;
    }
}
input[type='number'] {
 -moz-appearance:textfield;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
    -webkit-appearance: none;
}

 @media (max-width: 600px) {
     .product{
         flex-direction: column;
         align-items: center;
         max-width: 350px;
         &__buy{
             width: auto;
         }
     }
     .btn__wrapper{
         width: auto;
     }
 }
</style>