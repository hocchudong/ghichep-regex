##I. Giới thiệu chung
Regular Expression hay còn gọi là biểu thức chính quy được dùng để xử lý chuỗi nâng cao thông qua biểu thức riêng của nó, những biểu thức này sẽ có những nguyên tắc riêng và bạn phải tuân theo nguyên tắc đó thì biểu thức của bạn mới hoạt động được. Ngoài cái tên gọi Regular Expression ra thì nó còn có thể viết tắt thành RegEx.

RegEx rất hữu dụng trong việc trích dẫn thông tin từ văn bản như là code, logs file,... và được ứng dụng
vào nhiều service ( Graylog, Zabbix... ).

Tài liệu để học về RegEx có thể tham khảo trên trang : http://regexone.com/ hoặc

http://freetuts.net/cac-quy-tac-regular-expression-can-ban-65.html

Trang tham khảo để test các regex : https://regex101.com/ 

###Các quy tắc regular expression căn bản
 Một số khái niệm : 
 -  pattern: được gọi là chuỗi Regular Expression (biểu thức chính quy)
 -  subject: chuỗi so khớp với pattern
 
 Trong bài viết, các ví dụ đều sẽ được test trên trang: https://regex101.com/ 

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

#####3. Regex phạm vi của chuỗi

  *Regex kiểm tra chữ cái in thường* : <img src="http://i.imgur.com/mk29XdZ.png">
  
  *Regex kiểm tra chữ cái in hoa* : <img src="http://i.imgur.com/exTIDyY.png">
  
   Khi thay chuỗi test string bằng chữ in hoa, kết quả trả về sẽ là : <img src="http://i.imgur.com/exTIDyY.png">
  
  *Regex kiểm tra một ký tự là chữ số* : <img src="http://i.imgur.com/80g4xwk.png">
  
  *Regex kiểm một chữ cái in hoa hoặc in thường* : <img src="http://i.imgur.com/ERwSx6S.png">
  
  *Regex kiểm tra một ký tự là số, chữ cái in hoa hoặc thường* : <img src="http://i.imgur.com/nKhBbUn.png">
  
  *Regex kiểm tra ký tự có nằm trong dãy hay không* : <img src="http://i.imgur.com/DhkxgNN.png">
  
  Trong chuỗi subject, có một ký tự `"2"` nên kết quả trả về là `"Match"`
  
####4. Xác định chiều dài của chuỗi Regex
 *Regex kiểm tra chữ cái thường dài 5-10 ký tự* : <img src="http://i.imgur.com/fSr3fBF.png">
 
 Chuỗi subject='abcdef' đều là có các chữ cái in thường và có độ dài bằng 6 nên kết quả trả về sẽ là `"Match"`
 
 *Regex kiểm tra chuỗi có độ dài chính xác
 
 Cách 1 : <img src="http://i.imgur.com/cWVfGSN.png">
 
 Cách 2 : <img src="http://i.imgur.com/dNTPmEy.png">

####5. Regex đại diện cho một ký tự

Ký tự `"."` sẽ chấp nhận bất cứ ký tự nào,ví dụ : <img src="http://i.imgur.com/gGczvju.png">

Pattern này sẽ match với tất cả các subject có độ dài là 5. 



