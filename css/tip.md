1.
```css
div {
 width: 500px;
 height: 500px;
 padding: 20px
 border 5px solid red
 background-color: blue
}
```
=> width of div = width + border + padding = 500+20*2+5*2
If you want width always = 500px(include border and padding), you must use `box-sizing=border-box`

2. Khi dung `Float` luon nho can phai `clear float`
Cach de `clear float` la set thuoc tinh `overflow:auto` cho parrent box
Cach 2 la tao 1 the div lam diem dung o duoi div co float sau do set thuoc tinh `clear: both`

3. Khi text dai qua su dung `...`

```css
text-overflow: ellipsis;
white-space: nowrap;
```
