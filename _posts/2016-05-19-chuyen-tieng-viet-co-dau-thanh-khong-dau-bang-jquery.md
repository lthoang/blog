---
layout: post
title: "Chuyển tiếng Việt có sang chữ không dấu sử dụng jQuery"
description: ""
category: 
tags: []
---

# Tại sao cần chuyển tiếng Việt có dấu sang không dấu?

Vì hỗ trợ tìm kiếm từ 

Mã nguồn dùng để chuyển đổi tất cả các ký tự tiếng việt có dấu sang ký tự latin.

```javascript
var vietnameseToLatinCharacter = function (paragraph) {
  return paragraph
      .replace(/à|á|ạ|ả|ã|â|ầ|ấ|ậ|ẩ|ẫ|ă|ằ|ắ|ặ|ẳ|ẵ/g, "a")
      .replace(/À|Á|Ả|Ã|Ạ|Ă|Ằ|Ắ|Ẳ|Ẵ|Ặ|Â|Ầ|Ấ|Ẩ|Ẫ|Ậ/g, "A")
      .replace(/è|é|ẻ|ẽ|ẹ|ê|ề|ế|ể|ễ|ệ/g, "e")
      .replace(/È|É|Ẻ|Ẽ|Ẹ|Ê|Ề|Ế|Ể|Ễ|Ệ/g, "E")
      .replace(/ì|í|ỉ|ĩ|ị/g, "i")
      .replace(/Ì|Í|Ỉ|Ĩ|Ị/g, "I")
      .replace(/ò|ó|ỏ|õ|ọ|ô|ồ|ố|ổ|ỗ|ộ|ơ|ờ|ớ|ở|ỡ|ợ/g, "o")
      .replace(/Ò|Ó|Ỏ|Õ|Ọ|Ô|Ồ|Ố|Ổ|Ỗ|Ộ|Ơ|Ờ|Ớ|Ở|Ỡ|Ợ/g, "O")
      .replace(/ù|ú|ủ|ũ|ụ|ư|ừ|ứ|ử|ữ|ự/g, "u")
      .replace(/Ù|Ú|Ủ|Ũ|Ụ|Ư|Ừ|Ứ|Ử|Ữ|Ự/g, "U")
      .replace(/ỳ|ý|ỷ|ỹ|ỵ/g, "y")
      .replace(/Ỳ|Ý|Ỷ|Ỹ|Ỵ/g, "Y")
      .replace(/đ/g, "d")
      .replace(/Đ/g, "D");
}
```

Bonus: Đoạn mã này dùng để chuyển đổi tất cả các ký tự đặc biệt thành khoảng trắng.

```javascript
var specialCharacterToBlankSpace = function (paragraph) {
  return paragraph
      .replace(/,|.|\/|>|<|\?|;|:|'|"|`|~|!|@|#|$|%|^|&|\*|\(|\)|_|-|=|\+|[|]|\\/g, " ");
}
```

Nếu muốn giữ lại duy nhất một ký tự khoảng trắng giữa các từ thì sử dụng như sau:

```javascript
string.replace(/ +/g, " ");
```

# DEMO
<textarea id="in" style="width: 100%; height: 6em;" placeholder="Nhập chuỗi tiếng Việt ở đây"></textarea>
<br>
<textarea id="out" style="width: 100%; height: 6em;" placeholder="Kết quả"></textarea>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js"></script>
<script type="text/javascript">
  var vietnameseToLatinCharacter = function (string) {
    return string
      .replace(/à|á|ạ|ả|ã|â|ầ|ấ|ậ|ẩ|ẫ|ă|ằ|ắ|ặ|ẳ|ẵ/g, "a")
      .replace(/À|Á|Ả|Ã|Ạ|Ă|Ằ|Ắ|Ẳ|Ẵ|Ặ|Â|Ầ|Ấ|Ẩ|Ẫ|Ậ/g, "A")
      .replace(/è|é|ẻ|ẽ|ẹ|ê|ề|ế|ể|ễ|ệ/g, "e")
      .replace(/È|É|Ẻ|Ẽ|Ẹ|Ê|Ề|Ế|Ể|Ễ|Ệ/g, "E")
      .replace(/ì|í|ỉ|ĩ|ị/g, "i")
      .replace(/Ì|Í|Ỉ|Ĩ|Ị/g, "I")
      .replace(/ò|ó|ỏ|õ|ọ|ô|ồ|ố|ổ|ỗ|ộ|ơ|ờ|ớ|ở|ỡ|ợ/g, "o")
      .replace(/Ò|Ó|Ỏ|Õ|Ọ|Ô|Ồ|Ố|Ổ|Ỗ|Ộ|Ơ|Ờ|Ớ|Ở|Ỡ|Ợ/g, "O")
      .replace(/ù|ú|ủ|ũ|ụ|ư|ừ|ứ|ử|ữ|ự/g, "u")
      .replace(/Ù|Ú|Ủ|Ũ|Ụ|Ư|Ừ|Ứ|Ử|Ữ|Ự/g, "U")
      .replace(/ỳ|ý|ỷ|ỹ|ỵ/g, "y")
      .replace(/Ỳ|Ý|Ỷ|Ỹ|Ỵ/g, "Y")
      .replace(/đ/g, "d")
      .replace(/Đ/g, "D");
  }

  var specialCharacterToBlankSpace = function (string) {
    return string
        .replace(/,|\.|\/|>|<|\?|;|:|'|"|`|~|!|@|#|$|%|^|&|\*|\(|\)|_|-|=|\+|[|]|\\/g, " ");
  }

  var removeDuplicateWhiteSpaces = function (string) {
    return string.replace(/ +/g, " ");
  }

  $('#in').keyup(function () {
    $('#out').val(vietnameseToLatinCharacter(
      removeDuplicateWhiteSpaces(
        specialCharacterToBlankSpace(
          $(this).val()).trim())));
  });
</script>
