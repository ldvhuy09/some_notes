# Declarative Programming
## 1) What is Declarative Programming?

Trước tiên, cần hiểu ***Imperative programming:***
> **Imperative programming:** *telling the “machine” how to do something, and as a result what you want to happen will happen.*
***What does it mean???????????***
Đưa các lệnh lần lượt cho máy (dựa trên ngôn ngữ lập trình). Chương trình thực hiện các bước, và sẽ đưa ra kết quả cuối cùng.
- Các ngôn ngữ ***Imperative programming*** như C, C++, Java, .....
- Đỉnh cao của ***Imperative programming*** chính là OOP - đưa về các đối tượng để thực hiện (do something base on object).
Vậy còn ***Declarative programming:***
> **Declarative programming:** telling the “machine” what you would like to happen, and let the computer figure out how to do it.
***WTF?????***
Tức là chỉ cần quan tâm đầu vào, yêu cầu cần thực hiện, chương trình sẽ đưa ra kết quả cuối cùng.
***What is different ?????***
Chương trình nhân 2 các phần tử của mảng.
- **Imperative Programming** 
```javascript
//Imperative Programming 
var numbers = [1, 2, 3, 4, 5];
for (var i = 0; i < numbers.length; i++) {
    numbers[i] *= 2;
}
```
Phải duyệt mảng từ trên xuống dưới, mỗi phần từ nhân đôi lên.
- **Declarative programming**
```javascript
var numbers = [1, 2, 3, 4, 5];
var numbers_doubled = numbers.map(funtion(n) {
    return n * 2;
});
```
Khác biệt gì với Imperative Programming??? 
- Với Imperative Programming, ta phải thực hiện với low-level - duyệt từng phần từ và nhận đôi. Ta quan tâm đến 2 việc: duyệt từng phần từ + tại mỗi phần tử, ta thực hiện nhân đôi. 
- Với Declarative programming, ta chỉ cần quan nhân đôi từng phần từ, mọi thử còn lại thì method *map* đã xử lý *.*
## 2) Thiên thời - Địa lợi - Nhân hòa cho Declarative programming
### **Thiên thời** 
> Ý tưởng về Declarative programming đã cho từ những năm 50 của thế kỉ trước, với sự xuất hiện của **LISP** (Năm 1958)**.** Tuy nhiên khả năng máy tính lúc này còn nhiều giới hạn, vì vâỵ Declarative programming chưa thể phát triển mạnh.
Hiện nay, khả năng của máy tính đã phát triển vượt bậc, **thiên thời**  cũng từ đây:
- **Microsoft** ra mắt ngôn ngữ **F#**, phát triển bộ công cụ **RxExtension** cho .NET, Java, JS, C++, Python, Ruby… bây giờ là cả Swift nữa.
- **Netflix** sử dụng **RxJava** để viết lại JVM.
- **Github** sử dụng **ReactiveCocoa** để viết ứng dụng Github trên Mac OS X.
- **MS, AnguarJS**… sử dụng Declarative trong việc thiết kế giao diện (UI) cho ứng dụng: **XAML**
- **NewYork Times, Soundcloud, FourSquare**… rất nhiều công ty công nghệ sử dụng Declarative.
### **Địa lợi**
> **Functional Reactive Programming** thực ra là sự kết hợp của *Functional Programming* + *Reactive Programming*: 2 thành phần nhỏ thuộc Declarative.
- ***Reactive Programming***: cái này thì đơn giản thôi ạ, nếu ai làm .NET thì sẽ biết Data Binding, chính nó đấy ạ. Hiểu đơn giản thì: a = b + c. Khi b/c thay đổi thì giá trị của a cũng thay đổi theo, tự động, ngay tức thời.
- ***Functional Programming (FP)***: là phương thức giải quyết vấn đề bằng cách chia nhỏ vấn đề thành các function. Mỗi function lại có input là 1 function khác và output lại là 1 function. Trong quá trình kết nối các function, chúng hạn chế việc thay đổi các state cũng như không quy định rõ thứ tự của các function. Functional Programming coi chương trình như là 1 bài toán (math problem) chứ không phải là 1 chuỗi các thao tác (series operations).
***Các đặc điểm của FP:***
- First-Class Functions
- High-Order Functions
- Pure Functions
- Closures
- Immutable State
**Không cần quan tâm đến những cái tên là gì, bạn chỉ cần hiểu chúng là gì thôi!**
- First-Class Functions: bạn có thể lưu 1 function như 1 biến.
- High-Order Functions: Function có thể nhận input là 1 function và trả ra ouput cũng là 1 function.
- Pure Functions: Function không thay đổi bất kì biến nào. Nó chỉ đơn giản là nhận vào input và đưa ra output. Không thay đổi state, không tạo ra side-effects. Map, Reduce ở 2 ví dụ đầu tiên là pure function.
- Closures: Trong Objective-C nó là Block, Java là Lambda, Delegates trong C#… và dĩ nhiên là Closures trong rất nhiều ngôn ngữ khác :D.
### **Nhân hòa**
> Ngôn ngữ bạn đang dùng không cần là ngôn ngữ thuần **Functional Programming** như **Haskell, Erlang, Scala**…nhưng trên **Github** có sẵn các thư viện giúp bạn thực hiện điều đó. Cái tên **RxExtension – ReactiveX** của **MS** đáng được chú ý đầu tiên. Còn nếu bạn vẫn muốn có thêm bằng chứng thuyết phục, hãy đợi bài tiếp theo của tôi demo FRP trên **Objective-C/Swift** sử dụng **ReactiveCocoa/RxSwift.**

