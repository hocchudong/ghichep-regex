#Một số ghi chép chung về các quy tắc của Regex và ví dụ.
##Mục lục
####[1. Khai báo chuỗi Regex](#1)
####[2. Kí tự bắt đầu và kết thúc của chuỗi Regex](https://github.com/manhdinh/ghichep-regex/blob/master/Ghichep.md#2-kí-tự-bắt-đầu-và-kết-thúc-của-chuỗi-regex-1)
####[3. Regex phạm vi của chuỗi](https://github.com/manhdinh/ghichep-regex/blob/master/Ghichep.md#3-regex-phạm-vi-của-chuỗi-1)
####[4. Xác định chiều dài của chuỗi Regex](https://github.com/manhdinh/ghichep-regex/blob/master/Ghichep.md#4-xác-định-chiều-dài-của-chuỗi-regex-1)
####[5. Regex đại diện cho một ký tự](https://github.com/manhdinh/ghichep-regex/blob/master/Ghichep.md#5-regex-đại-diện-cho-một-ký-tự-1)
####[6. Ký tự đặc biệt cho các từ khóa Regex](https://github.com/manhdinh/ghichep-regex/blob/master/Ghichep.md#6-ký-tự-đặc-biệt-cho-các-từ-khóa-regex-1)
####[7. Regex A hoặc B](https://github.com/manhdinh/ghichep-regex/blob/master/Ghichep.md#7-regex-a-hoặc-b-1)
####[8.  Regex kiểm tra chiều dài không giới hạn](https://github.com/manhdinh/ghichep-regex/blob/master/Ghichep.md#8--regex-kiểm-tra-chiều-dài-không-giới-hạn-1)
####[9. Capturing value trong Regex](https://github.com/manhdinh/ghichep-regex/blob/master/Ghichep.md#9-capturing-value-trong-regex-1)
####[10. Greedy trong Regex](https://github.com/manhdinh/ghichep-regex/blob/master/Ghichep.md#10-greedy-trong-regex-1)
####[11. Một số ví dụ về áp dụng Regex vào Graylog](https://github.com/manhdinh/ghichep-regex/blob/master/Ghichep.md#11-một-số-ví-dụ-về-áp-dụng-regex-vào-graylog-1)
## Giới thiệu chung
Regular Expression (Regex) hay còn gọi là biểu thức chính quy được dùng để xử lý chuỗi nâng cao thông qua biểu thức riêng của nó, những biểu thức này sẽ có những nguyên tắc riêng và bạn phải tuân theo nguyên tắc đó thì biểu thức của bạn mới hoạt động được. 

Regex rất hữu dụng trong việc trích dẫn thông tin từ văn bản như là code, logs file,... và được ứng dụng
vào nhiều service ( Graylog, Zabbix... ).

Tài liệu để học về Regex có thể tham khảo trên trang : http://regexone.com/ hoặc

http://freetuts.net/cac-quy-tac-regular-expression-can-ban-65.html

Trang tham khảo để test các regex : https://regex101.com/ 

###Các quy tắc regular expression căn bản
 Một số khái niệm : 
 -  pattern: được gọi là chuỗi Regular Expression (biểu thức chính quy)
 -  subject: chuỗi so khớp với pattern
 
 Trong bài viết, các ví dụ đều sẽ được test trên trang: https://regex101.com/ 

<a name="1"></a>
####1. Khai báo chuỗi Regex
 Để khai báo một chuỗi Regular Expression ta chỉ cần khai báo bắt đầu bằng ký tự / và kết thúc cũng là ký tự /.
 
 Ví dụ: 
 
pattern = '/abc/';
 
subject = 'abc';

Khi test chuỗi thì có kết quả như sau : <img src="http://i.imgur.com/UImXGkP.png">

Trong ví dụ này, pattern = `'abc'` có ý nghĩa là tìm xem trong chuỗi subject này có chuỗi `abc` hay không, ta thấy kết quả khi test,mũi tên số 3 trả về kết quả là *Match* , bởi vì chuỗi subject='abc'

Bây giờ ta sẽ đổi giá trị của subject='mabcde', kết quả test sẽ là : <img src="http://i.imgur.com/r28t9ZS.png">

Kết quả ở đây vẫn là *Match* , bởi chuỗi `'mabcde'` khi chia nhỏ ra vẫn chứa chuỗi `'abc'`.

####2. Kí tự bắt đầu và kết thúc của chuỗi Regex

Khi muốn kiểm tra xem chuỗi trong pattern có trùng khớp hoàn toàn với chuỗi trong subject không, ta sẽ dùng ký tự bắt đầu `^` và ký tự kết thúc `$` đặt vào đầu và cuối chuỗi pattern.

Ví dụ 1: <img src="http://i.imgur.com/TwadzCF.png">

Kết quả trả về là *Match* vì chuỗi trong pattern và subject trùng khớp. 

Ví dụ 2: <img src="http://i.imgur.com/ZL9AAYO.png">

Kết quả trả về sẽ là *No match* vì chuỗi subject đã bị thêm những ký tự khác.

####3. Regex phạm vi của chuỗi

  <li>Regex kiểm tra chữ cái in thường:</li> <img src="http://i.imgur.com/mk29XdZ.png">
  
  <li>Regex kiểm tra chữ cái in hoa:</li> <img src="http://i.imgur.com/exTIDyY.png">
  
   Khi thay chuỗi test string bằng chữ in hoa, kết quả trả về sẽ là : <img src="http://i.imgur.com/exTIDyY.png">
  
  <li>Regex kiểm tra một ký tự là chữ số: </li> <img src="http://i.imgur.com/80g4xwk.png">
  
  <li>Regex kiểm một chữ cái in hoa hoặc in thường:</li>  <img src="http://i.imgur.com/ERwSx6S.png">
  
  <li>Regex kiểm tra một ký tự là số, chữ cái in hoa hoặc thường:</li>  <img src="http://i.imgur.com/nKhBbUn.png">
  
  Trong chuỗi subject, có một ký tự `"2"` nên kết quả trả về là `"Match"`
  
  Ví dụ : Khi ta muốn Match với cả 3 từ trong ô vuông đỏ, và bỏ qua các từ còn lại thì pattern sẽ được viết dưới dạng như sau : <img src="http://i.imgur.com/yne1i6K.png">
  
   <li>Regex kiểm tra ký tự có nằm trong dãy hay không</li> : <img src="http://i.imgur.com/DhkxgNN.png">
   hoặc khi ta đặt dấu `^` ở trước chuỗi, thì regex sẽ mang tính phủ định : <img src="http://i.imgur.com/MniYaOZ.png">
   
   Biểu thức sẽ Match với ký tự đầu tiên không phải là các ký tự `a` `2` `b`
   
  Ví dụ : Khi ta muốn Match với 3 từ trong ô vuông đỏ, và bỏ qua các từ còn lại, thì pattern sẽ là : <img src="http://i.imgur.com/0XHuq2y.png"> hoặc <img src="http://i.imgur.com/rtI25iB.png">
  
####4. Xác định chiều dài của chuỗi Regex
 *Regex kiểm tra chữ cái thường dài 5-10 ký tự* : <img src="http://i.imgur.com/fSr3fBF.png">
 
 Chuỗi subject='abcdef' đều là có các chữ cái in thường và có độ dài bằng 6 nên kết quả trả về sẽ là `"Match"`
 
 *Regex kiểm tra chuỗi có độ dài chính xác*
 
 Cách 1 : <img src="http://i.imgur.com/cWVfGSN.png">
 
 Cách 2 : <img src="http://i.imgur.com/dNTPmEy.png">
 
 Ví dụ : Khi muốn Match với 2 từ trong ô vuông đỏ và bỏ qua từ còn lại, pattern sẽ là : <img src="http://i.imgur.com/IV97Kss.png">

####5. Regex đại diện cho một ký tự

Ký tự `"."` sẽ chấp nhận bất cứ ký tự nào,ví dụ : <img src="http://i.imgur.com/gGczvju.png">

Pattern này sẽ match với subject='1s#5c' vì chuỗi `1s#5c'` có độ dài bằng 5

####6. Ký tự đặc biệt cho các từ khóa Regex

Tất cả các ký tự như : `.`, `[]`, `{}`...những ký tự liên quan đến quy tắc của Regex đều được quy về dạng ký tự đặc biệt trong Regex, vì vậy để phân biệt giữa ký tự đặc biệt trong Regex và ký tự bình thường thì ta thêm dấu `\` vào đầu ký tự đó.

Ví dụ, khi kiểm tra trong subject='demo' có xuất hiện dấu `.` hay không?, nếu ta kiểm tra như sau : <img src="http://i.imgur.com/MeVYA6f.png">

Kết quả trả về là `Match`, tuy nhiên như vậy không đúng bởi trong chuỗi subject='demo' không hề có dấu `.` nào cả, pattern đang bị hiểu nhầm dấu `.` tương đương với ký tự `d`. Biểu thức pattern đúng phải là như sau : <img src="http://i.imgur.com/vCtVAHB.png">

####7. Regex A hoặc B

Khi cần kiểm tra subject='A' hoặc subject='B' thì ta cần dùng dấu `|`, biểu diễn mối quan hệ `OR`

Ví dụ : Khi muốn match với 2 từ tỏng ô vuông đỏ, và bỏ qua các từ còn lại, pattern sẽ là : <img src="http://i.imgur.com/BrGwkeR.png">
####8.  Regex kiểm tra chiều dài không giới hạn

*Các ký tự Regex đặc biệt:*

 - \d - Chữ số bất kỳ ~ [0-9]
 - \D - Ký tự bất kỳ không phải là chữ số (ngược với \d) ~ [^0-9]
 - \w - Ký tự từ a-z, A-Z, hoặc 0-9 ~ [a-zA-Z0-9]
 - \W - Ngược lại với \w (nghĩa là các ký tự không thuộc các khoảng: a-z, A-Z, hoặc 0-9) ~[^a-zA-Z0-9]
 - \s - Khoảng trắng (space)
 - \S - Ký tự bất kỳ không phải là khoảng trắng.

Sử dụng các ký tự `*`, `+`, `?` để thiết lập chiều dài cho chuỗi.

<li>Ký tự`*`</li>
Dấu `*` đại diện cho không hoặc nhiều ký tự, <img src="http://i.imgur.com/zOc8llE.png">
Chuỗi pattern này sẽ chỉ lọc những ký tự chữ cái thường của subject
<li>Ký tự`+`</li>
Dấu `+` đại diện cho một hoặc nhiều ký tự, <img src="http://i.imgur.com/kT46NnL.png">
Chuỗi pattern này cũng sẽ lọc tất cả những chữ cái thường của subject

Ví dụ : Khi muốn Match với 3 từ trong ô vuông đỏ và bỏ qua từ cuối cùng, pattern sẽ là : <img src="http://i.imgur.com/IhDbpPy.png">

Phân tích pattern : 
 - `aa+` : Các từ được Match phải có ít nhất 2 ký tự `a` trở lên => Mẫu cuối chỉ có 1 ký tự `a` nên không thỏa mãn
 - `b*`  : Không có hoặc có nhiều hơn 1 ký tự `b` , nên mẫu thứ 3 tuy không có ký tự `b` nào nhưng vẫn thỏa mãn pattern
 - `c+`  : Có một hoặc nhiều hơn một ký tự `c`
<li>Ký tự `?` </li>
Dấu `?` đại diện cho một hoặc không có ký tự nào, <img src="http://i.imgur.com/Ri9zWZk.png">

Ví dụ : Khi muốn Match với 3 từ trong ô vuông đỏ và bỏ qua từ cuối cùng, pattern sẽ là : <img src="http://i.imgur.com/BjODc7m.png">

Phân tích pattern : 
 - `\d+ `    : Sẽ match với các chữ số ở đầu và ký tự khoảng trống ` `
 - `files? ` : Sẽ match với từ `file` với một hoặc không có ký tự `s` và ký tự khoảng trống ` `
 - `found\?`  : Sẽ match với từ `found` và ký tự `?`, bởi ký tự `?` sẽ bị hiểu như một ký tự đặc biệt của regex nên ta phải thêm `\` ở đằng trước để tránh bị regex hiểu nhầm

####9. Capturing value trong Regex

<li>Caturing value, hiểu đơn giản là các bắt các giá trị muốn có một subject.</li>

Ví dụ 1 : Ta có chuỗi pattern="([a-z]+)([0-9]+)" 
<img src="http://i.imgur.com/8JB7spj.png"> 

Pattern này sẽ có 3 phần : 
 - Phần 1 : ([a-z]+)([0-9]+) sẽ bắt tất cả dòng `manhdv1994`
 - Phần 2 : ([a-z]+) sẽ bắt tất cả các ký tự chữ cái thường.
 - Phần 3 : ([0-9]+) sẽ bắt cả các số đằng sau các chữ cái thường.
 <li> Caturing Sub-group 
Ví dụ khi ta muốn bắt 2 nhóm như trong hình, pattern sẽ là : <img src="http://i.imgur.com/ZWlxqcY.png">
 
Ví dụ 2 : Khi ta chỉ muốn bắt phần tên của file, pattern sẽ là : <img src="http://i.imgur.com/thIxT7B.png">
####10. Greedy trong Regex

Trước khi có một định nghĩa về Greedy, tôi sẽ lấy một ví dụ sau về việc tìm chuỗi bắt đầu bằng `h` và kết thúc bằng `o`
<img src="http://i.imgur.com/akD4IWH.png">

Ý tưởng ban đầu của regex này sẽ là lấy được cụm `ell` ở trong từ `hello`, tuy nhiên ở chữ `chao` lại có 1 ký tự `o`, nên chuỗi regex sẽ hiểu là lấy chuỗi bắt đầu bằng `h` của hello, và kết thúc bằng `o` của `chao`, muốn chỉ lấy được từ `ell` ta phải đặt chuỗi pattern như sau : <img src="http://i.imgur.com/gmYBPdD.png">

####11. Một số ví dụ về áp dụng Regex vào Graylog

*Khi muốn bắt thông tin về id=9733 của sshd như trong hình sau:*
<img src="http://i.imgur.com/ULLQiN8.png">
*Khi muốn bắt thông tin về user đăng nhập ssh:*
<img src="http://i.imgur.com/6iPV4cP.png">
*Khi muốn bắt thông tin về ip đăng nhập ssh:*
<img src="http://i.imgur.com/8CxpG5e.png">
*Khi muốn bắt thông tin về port đăng nhập ssh:*
<img src="http://i.imgur.com/6S5xDgQ.png">

