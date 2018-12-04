# Twitter

---

Twitterタイムラインの埋め込み。

---

## HTML

```html
<div class="js-twitter" data-twitter-id="twitterID" data-twitter-width="540" data-twitter-height="800"></div>
```

## Javascript

### 関数

```javascript
const WriteTwitterWidget = {
  wrap: '.js-wrap',
  elem: '.js-twitter',
  id: '',
  script () {
    let script = document.createElement('script');
    script.src = 'https://platform.twitter.com/widgets.js';
    $(this.wrap).append(script);
  },
  get () {
    $(this.elem).each((index, e) => {
      let id = $(e).attr('data-twitter-id');
      let chrome = $(e).attr('data-twitter-chrome') || 'noheader nofooter noscrollbar noborders transparent';
      let width = $(e).attr('data-twitter-width') || 500;
      let height = $(e).attr('data-twitter-height') || 700;
      this.init(e, id, chrome, width, height);
    });
  },
  init (e, id, chrome, width, height) {
    let _iframe = `<a class="twitter-timeline" width="${width}" height="${height}" data-chrome="${chrome}" href="https://twitter.com/${id}?ref_src=twsrc%5Etfw"></a>`
    $(e).append(_iframe);
  },
  init () {
    this.script();
    this.get();
  }
};
```

### 宣言  

```javascript
WriteTwitterWidget.init();
```

### メソッド

```javascript
```