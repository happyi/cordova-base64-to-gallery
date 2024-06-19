# Cordova ImgToGallery Plugin
============================
forked from Nexxa/cordova-base64-to-gallery

# SetUp 

cordova plugin add cordova-plugin-mz-img-to-gallery

# Usage
```javascript
function getBase64Image(img) {
    var canvas = document.createElement("canvas");
    canvas.width = img.width;
    canvas.height = img.height;
    var ctx = canvas.getContext("2d");
    ctx.drawImage(img, 0, 0, img.width, img.height);
    var dataURL = canvas.toDataURL("image/png");
    return dataURL;
}
var tempImage = new Image();
tempImage.src = "https://图片地址"
tempImage.crossOrigin = "*";
tempImage.onload = function()
{
    var base64Data = getBase64Image(tempImage);
    cordova.base64ToGallery(base64Data,
        {
            prefix: 'cordova_', // 图片前缀
            mediaScanner: true // 保存成功通知相册刷新
        },
        function(path) {
            console.log("已保存到相册",path);
        },
        function(err) {
            console.error("savePhoto->保存失败:"+JSON.stringify(err),"error")
        }
    );
}
```
