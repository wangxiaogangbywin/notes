### 下载图片

[filesaver.js]: https://github.com/eligrey/FileSaver.js

a 标签的 download 属性有局限性
可以用 [FileSaver.js] 实现下载

### 例子

```
import { saveAs } from 'file-saver/FileSaver';

export const downloadImg = (url) => {
  const img = new Image();
  img.crossOrigin = 'Anonymous';
  function download() {
    let canvas = document.createElement('CANVAS');
    const ctx = canvas.getContext('2d');
    canvas.height = this.height;
    canvas.width = this.width;
    ctx.drawImage(this, 0, 0);
    canvas.toBlob((blob) => {
      saveAs(blob, '下载图片.png');
    });
    canvas = null;
  }
  img.onload = download;
  img.url = imgUrl;
}
```
