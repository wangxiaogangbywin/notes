### 前端图片转 base64

我感觉没啥用的功能，但是竟然被要求做了。。。
用 canvas 的 toDataURL 就实现了

### 例子

```
export const downloadImg = (url,callback) => {
  const img = new Image();
  img.crossOrigin = 'Anonymous';
  img.onload = () => {
    let canvas = document.createElement('CANVAS');
    const ctx = canvas.getContext('2d');
    canvas.height = img.height;
    canvas.width = img.width;
    ctx.drawImage(img, 0, 0);
    const base64 = canvas.toDataURL('image/jpeg');
    callback(base64);
    canvas = null;
  };
  img.src = url;
}
```
