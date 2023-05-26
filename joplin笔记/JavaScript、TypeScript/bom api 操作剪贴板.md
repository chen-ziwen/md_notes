```javascript
// 复制剪贴板内容
function copy(songName: string) {
    if (navigator.clipboard) {
        navigator.clipboard.writeText(songName);
    }
}
```