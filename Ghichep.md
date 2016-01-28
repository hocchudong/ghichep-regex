##I. Giới thiệu chung
Regular Expression hay còn gọi là biểu thức chính quy được dùng để xử lý chuỗi nâng cao thông qua biểu thức riêng của nó, những biểu thức này sẽ có những nguyên tắc riêng và bạn phải tuân theo nguyên tắc đó thì biểu thức của bạn mới hoạt động được. Ngoài cái tên gọi Regular Expression ra thì nó còn có thể viết tắt thành RegEx.

RegEx rất hữu dụng trong việc trích dẫn thông tin từ văn bản như là code, logs file,... và được ứng dụng
vào nhiều service ( Graylog, Zabbix... ).

Tài liệu để học về RegEx có thể tham khảo trên trang : http://regexone.com/ hoặc http://freetuts.net/cac-quy-tac-regular-expression-can-ban-65.html
Trang tham khảo để test các regex : https://regex101.com/ 

###Các quy tắc regular expression căn bản
 Một số khái niệm : 
 -  pattern: được gọi là chuỗi Regular Expression (biểu thức chính quy)
 -  subject: chuỗi so khớp với pattern
 Trong bài viết, các ví dụ đều sẽ được test trên trang: https://regex101.com/ 
 Ví dụ như sau : <img src="http://i.imgur.com/YaqjXpG.png">

####1. Khai báo chuỗi RegEx
 Để khai báo một chuỗi Regular Expression ta chỉ cần khai báo bắt đầu bằng ký tự / và kết thúc cũng là ký tự /.
  Ví dụ: 
    pattern = '/abc/';
    subject = 'abc';
    Khi test chuỗi thì có kết quả như sau : <img src="http://i.imgur.com/WrSupg6.png">
Trong ví dụ này, pattern = `'abc'` có ý nghĩa là tìm xem trong chuỗi subject này có chuỗi `abc` hay không, ta thấy kết quả khi test, dòng `abc` được bôi đậm, nghĩa là kết quả trả về ở đây là đúng, bởi vì chuỗi subject='abc'

