# Modal

---

モーダル

---

## HTML

```html
<div class="l-modal js-modal">
    <div class="l-modal__bg js-modal__close"></div>
    <div class="l-modal__container js-modal__container">
      <div class="l-modal__inner js-modal__inner">

      </div>
    </div>
    <div class="l-modal__close js-modal__close">

    </div>
  </div>
</div>
```

## Javascript

### 関数

```javascript
 class Modal{
    constructor() {
      this.conf = {
        wrap: '.js-wrap',
        elem: '.js-modal',
        container: '.js-modal__container',
        inner: '.js-modal__inner',
        open: '.js-modal__open',
        close: '.js-modal__close',
        position: undefined,
        speed: 850,
      };
      this.init();
    }
    view(abs = false) {
      if(abs){
        this.position();
      }
      $(this.conf.elem).addClass('is-modal-open');
      $(this.conf.container).css({'top': this.conf.position});
      // $(this.conf.elem).fadeIn(this.conf.speed, 'easeOutQuart');
    }
    hide() {
      $(this.conf.elem).removeClass('is-modal-open');
      // $(this.conf.elem).fadeOut(this.conf.speed, 'easeOutQuart');
    }
    scroll() {
      $('html,body').animate({
        scrollTop: this.conf.position
      }, 0);
    }
    position() {
      this.conf.position = window.pageYOffset;
    }
    click() {
      $(this.conf.wrap).on('click', this.conf.open, (e) => {
        // open event
        this.view(false);
        this.openCallback(e.currentTarget);
      });
      $(this.conf.wrap).on('click', this.conf.close, (e) => {
        this.hide();
        // close event
        this.closeCallback(e.currentTarget);
        //this.scroll();
      });
    }
    openCallback(e) {
    }
    closeCallback(e) {
    }
    resize() {
      $(window).on('resize', () => {
        this.position();
      });
    }
    init() {
      this.click();
      this.resize();
    }
  }
```

### 宣言  

```javascript
const modal = new Modal();
```

### メソッド

```javascript
```
### 継承

```javascript

  class ExtendModal extends Modal{
    constructor() {
      super();
    }
    openCallback(e) {
    }
    closeCallback(e) {
    }
  }
  
 const extendModal = new ExtendModal();

```
