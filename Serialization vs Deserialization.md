# Serialization vs Deserialization
## 1) Serialization và Deserialization là gì?
- **Serialization** là khả năng của *object* có thể => *mảng bytes.*
- **Deserialization** là chuyển *mảng bytes* thành *object*.
## 2) Why they exist?
### * Cách lưu object xuống file?
**Trivial Solution:**  Lưu từng thuộc tính xuống file => **HAVE SOME PROBLEMS:**
- Không thể biết bao nhiều thuộc tính.
- Khó khăn khi đọc lại.
**=> How to solve the problems????**
**=> Serialization vs Deserialization.**
> **Tóm lại: Do cần một GIAO THỨC CHUNG khi giao tiếp các *object* với nhau.**
## 3) How to use them?
Kế thừa 1 class có khả năng Serialization, hoặc kế thức trực tiếp **interface** *Java.io.Serializable*
For example:
```java
public class Employee implements java.io.Serializable {
	public String name;
	public String address;
	public transient int SSN;
	public int number;

	public void mailCheck() {
		System.out.println("Mailing a check to " + name + " " + address);
	}
}
```
Bây giờ class Employee có khả năng Serialization (tức là Serializable).
## 4) Lưu ý
- Khi sử dựng khả năng Serialization, phải implement java.io.Serializable interface, nếu không java.io.NotSerializableException sẽ xảy ra.
- Nếu superclass là Serializable thì các lớp con của nó sẽ tự động được Serializable.
- Tất cả attribute phải serializable, không thì phải có từ khóa transient trước nó (trong example).
- Bạn không thể serialize các biến static
### 5) Tham khảo:
> https://viblo.asia/p/java-serialization-XL6lAYrDlek 