
<script>
    export default {
        name: 'ProductCard',
        props: {
            poster_path: String,
            title: String,
            original_title: String,
            original_language: String,
            vote_average: Number,
            name: String,
            original_name: String,
            product: Object,
        },
        data() {
            return {
                hover: false
            }
        },
        computed: {
            vote(){
                return Math.ceil(this.product.vote_average / 2)

            }
        }
    }
</script>

<template>
    <div class="col mb-3">
       
        <figure  @mouseover="hover = true" @mouseleave="hover = false">
            <img v-if="product.poster_path" class="poster" :src="`https://image.tmdb.org/t/p/w342/${product.poster_path}`" :alt="product.title">
            <img v-else src="https://www.altavod.com/assets/images/poster-placeholder.png" class="poster" alt="placeholder image">


            <div v-if="hover" class="content-hvr h-100 w-100 d-flex flex-column  p-2">
                <div>
                    <h4 class="text-danger fw-bold">
                        {{ product.title || product.name }}        
                    </h4>
                    <h6>
                      Original title: "{{ product.original_title || product.original_name }}"    
                    </h6>
                </div>
                <div >
                    Original language:
                    <img v-if="product.original_language === 'it' || product.original_language === 'en'" class="img-fluid flag" :src="`/src/assets/img/${product.original_language}.png`" :alt="product.original_language">
                    <span class="fw-bold" v-else>{{ product.original_language.toUpperCase() }}</span>
                </div>
                
                <div>
                    
                    <div>
                        <i v-for="star in 5" :class="star <= vote ? 'fa-solid' : 'fa-regular'" class="fa-star"></i>
                    </div>

                    <div>
                        <h5> Overview:</h5>
                        <p>
                            {{ product.overview }}
                        </p>           
                    </div>

                </div>
            </div>
        </figure>   
    </div>
   

</template>

<style lang="scss" scoped>
   .flag {
  height: 25px;
}

figure {
    position: relative;

    .poster {
    height: 350px;
    width: 240px;
    cursor: pointer;
    }

    .content-hvr {
                cursor: pointer;
                position: absolute;
                top: 0;
                left: 0;
                color: white;
                background-color: rgba(0, 0, 0, 0.8);
                overflow-y: auto;
                overflow-x: hidden;
                // width: 235px;
                // min-height: 350px;

                p {
                    font-size: 12px;
                }

                 *{
                 padding: 5px 0;
             }
    }
}

.fa-solid {
    color: #dc3545;
}

  
</style>