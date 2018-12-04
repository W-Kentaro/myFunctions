# Scroll Function

---

ページ内スクロール。  
aタグとdata属性に対応。  
(data属性推奨)

---

## HTML

```html
<div data-scroll="top"></div>
```

## Javascript

### 関数

```javascript
const Scroll = {
  conf: {
    elem: '[data-scroll]'
  },
  data(e, target = false, speed) {
    const dataScroll = e ? e.attr('data-scroll') : null;
    let destination = target ? '#' + target : '#' + dataScroll;
    if(dataScroll === 'top'){
      destination = 'body';
    }
    const scrollHeight = $(destination).offset().top;
    this.scroll(scrollHeight, speed);
  },
  hash: (e) => {
    let href = $(e).attr('href');
    let target = $(href == '#' || href == '' ? 'html' : href);
    let position = target.offset().top;
    this.scroll(position);
  },
  scroll(position, speed = 950) {
    $('html,body').animate({
      scrollTop: position
    }, speed, 'easeOutQuad');
  },
  click() {
    $(this.conf.elem).on('click', (e) => {
      this.data($(e.currentTarget));
    });
    $('a[href^="#"]').on('click', (e) => {
      this.hash(e.currentTarget);
    });
  },
  act(target, speed) {
    this.data(false, target, speed);
  },
  default() {
    this.click();
  }
};
```

### 宣言  

```javascript
Scroll.default();
```

### メソッド

スクロールさせる場所とスピードを指定可

```javascript
Scroll.act(target, speed);
```