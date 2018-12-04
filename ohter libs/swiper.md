# Swiper Function  

---

Swiperのスライド設定。  
オブジェクトとメソッドで管理して、
宣言前の変更等に適応させたものになります。  

need =>  http://idangero.us/swiper/


---

## HTML

```html
<div class="swiper-container js-slide">
  <div class="swiper-wrapper">
   <div class="swiper-slide"></div>
  </div>
</div>
```

## Javascript

### 関数


```javascript
const Slide = {
  elem: '.js-slide',
  slide: undefined,
  props: {
    init: false,
    speed: 600,
    direction: 'horizontal',
    slidesPerView: 1,
    spaceBetween: 0,
    breakpointsInverse: true,
    loop: true,
    slideActiveClass: 'is-current',
    slideNextClass: 'is-next',
    slidePrevClass: 'is-prev',
    breakpoints: {
      768: {}
    },
    // use nav
    navigation: {
      nextEl: '.js-slide__btn--next',
      prevEl: '.js-slide__btn--prev',
    },
    on: {
      init() {
      },
      slideChange() {
      },
      onSlideChangeEnd() {
        this.update(true);
      }
    },
  },
    set() {
      this.define();
      this.slide.init();
    },
    define() {
      this.slide = new Swiper(this.elem, this.props);
    },
    click() {
      $(`${this.elem}__slide`).on('click', (e) => {
      });
    },
    resize() {
      $(window).on('resize', () => {
        this.slide.init();
      });
    },
    init() {
      if($(`${this.elem}__slide`).length > 1){
        this.get();
        this.set();
        this.resize();
      }
    }
};
```


### 宣言  

```javascript
Slide.init();
```
