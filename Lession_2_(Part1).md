# **BÀI 2: LÀM QUEN VỚI NGÔN NGỮ DART (Phần 1)**

Sau khi tìm hiểu một số thông tin về Dart, những ưu điểm và cách cài đặt Dart
thông qua bài 1. Ta sẽ tiếp tục làm quen với ngôn ngữ này.

Bài được chia thành 2 phần, trong phần đầu tiên ta cần biết những nội dung sau:

-   Từ khoá trong Dart?

-   Cách khai báo, khởi tạo biến?

-   Hằng số - Cách khai báo, sử dụng?

-   Các kiểu dữ liệu trong Dart?

## **TỪ KHOÁ**

Bảng sau liệt kê các từ mà ngôn ngữ Dart xử lý đặc biệt:

| [abstract](https://dart.dev/guides/language/language-tour#abstract-classes) 2         | [dynamic](https://dart.dev/guides/language/language-tour#important-concepts) 2             | [implements](https://dart.dev/guides/language/language-tour#implicit-interfaces) 2                      | [show](https://dart.dev/guides/language/language-tour#importing-only-part-of-a-library) 1 |
|---------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| [as](https://dart.dev/guides/language/language-tour#type-test-operators) 2            | [else](https://dart.dev/guides/language/language-tour#if-and-else)                         | [import](https://dart.dev/guides/language/language-tour#using-libraries) 2                              | [static](https://dart.dev/guides/language/language-tour#class-variables-and-methods) 2    |
| [assert](https://dart.dev/guides/language/language-tour#assert)                       | [enum](https://dart.dev/guides/language/language-tour#enumerated-types)                    | [in](https://dart.dev/guides/language/language-tour#for-loops)                                          | [super](https://dart.dev/guides/language/language-tour#extending-a-class)                 |
| [async](https://dart.dev/guides/language/language-tour#asynchrony-support) 1          | [export](https://dart.dev/guides/libraries/create-library-packages) 2                      | [interface](https://stackoverflow.com/questions/28595501/was-the-interface-keyword-removed-from-dart) 2 | [switch](https://dart.dev/guides/language/language-tour#switch-and-case)                  |
| [await](https://dart.dev/guides/language/language-tour#asynchrony-support) 3          | [extends](https://dart.dev/guides/language/language-tour#extending-a-class)                | [is](https://dart.dev/guides/language/language-tour#type-test-operators)                                | [sync](https://dart.dev/guides/language/language-tour#generators) 1                       |
| [break](https://dart.dev/guides/language/language-tour#break-and-continue)            | [external](https://stackoverflow.com/questions/24929659/what-does-external-mean-in-dart) 2 | [library](https://dart.dev/guides/language/language-tour#libraries-and-visibility) 2                    | [this](https://dart.dev/guides/language/language-tour#constructors)                       |
| [case](https://dart.dev/guides/language/language-tour#switch-and-case)                | [factory](https://dart.dev/guides/language/language-tour#factory-constructors) 2           | [mixin](https://dart.dev/guides/language/language-tour#adding-features-to-a-class-mixins) 2             | [throw](https://dart.dev/guides/language/language-tour#throw)                             |
| [catch](https://dart.dev/guides/language/language-tour#catch)                         | [false](https://dart.dev/guides/language/language-tour#booleans)                           | [new](https://dart.dev/guides/language/language-tour#using-constructors)                                | [true](https://dart.dev/guides/language/language-tour#booleans)                           |
| [class](https://dart.dev/guides/language/language-tour#instance-variables)            | [final](https://dart.dev/guides/language/language-tour#final-and-const)                    | [null](https://dart.dev/guides/language/language-tour#default-value)                                    | [try](https://dart.dev/guides/language/language-tour#catch)                               |
| [const](https://dart.dev/guides/language/language-tour#final-and-const)               | [finally](https://dart.dev/guides/language/language-tour#finally)                          | [on](https://dart.dev/guides/language/language-tour#catch) 1                                            | [typedef](https://dart.dev/guides/language/language-tour#typedefs) 2                      |
| [continue](https://dart.dev/guides/language/language-tour#break-and-continue)         | [for](https://dart.dev/guides/language/language-tour#for-loops)                            | [operator](https://dart.dev/guides/language/language-tour#overridable-operators) 2                      | [var](https://dart.dev/guides/language/language-tour#variables)                           |
| [covariant](https://dart.dev/guides/language/sound-problems#the-covariant-keyword) 2  | [Function](https://dart.dev/guides/language/language-tour#functions) 2                     | [part](https://dart.dev/guides/libraries/create-library-packages#organizing-a-library-package) 2        | [void](https://medium.com/dartlang/dart-2-legacy-of-the-void-e7afb5f44df0)                |
| [default](https://dart.dev/guides/language/language-tour#switch-and-case)             | [get](https://dart.dev/guides/language/language-tour#getters-and-setters) 2                | [rethrow](https://dart.dev/guides/language/language-tour#catch)                                         | [while](https://dart.dev/guides/language/language-tour#while-and-do-while)                |
| [deferred](https://dart.dev/guides/language/language-tour#lazily-loading-a-library) 2 | [hide](https://dart.dev/guides/language/language-tour#importing-only-part-of-a-library) 1  | [return](https://dart.dev/guides/language/language-tour#functions)                                      | [with](https://dart.dev/guides/language/language-tour#adding-features-to-a-class-mixins)  |
| [do](https://dart.dev/guides/language/language-tour#while-and-do-while)               | [if](https://dart.dev/guides/language/language-tour#if-and-else)                           | [set](https://dart.dev/guides/language/language-tour#getters-and-setters) 2                             | [yield](https://dart.dev/guides/language/language-tour#generators) 3                      |

Bạn không thể dụng những `keyword` (từ khoá) này như một `identifier` (tên biến,
hàm…). Tham khảo thêm [tại
đây.](https://dart.dev/guides/language/language-tour#keywords)

## **KHAI BÁO – KHỞI TẠO BIẾN**

Biến để lưu các đối tượng khi ứng dụng hoạt động, để tạo ra biến dùng từ khóa
`var` (optional variable) với cú pháp như sau.

```dart
	main() {
	    // Khai báo biến a, khởi tạo nó lưu một chuỗi
	    // (do vậy a có kiểu String, nó chỉ lưu chuỗi)
	    var a = "Learn Dart";
	    a = "Learn Dart 2";   // Gán chuỗi khác
	    a = 100;              // Lỗi Compile-time vì gán số vào a
	    // Khai báo và không khởi tạo
	    // biến b sẽ có giá trị null - lúc này
	    // kiểu của b tùy thuộc vào giá trị gán vào nó
	    var b;
	    b = 100;            // Gán số vào b
	    b = "aaa";          // Gán chuỗi vào b
}
```


Bạn cũng có thể khai báo và chỉ định kiểu dữ liệu cụ thể cho nó luôn, khi chỉ
định kiểu cụ thể mỗi khi gán dữ liệu vào biến thì giá trị phải cùng kiểu

```dart
	String  s     = 'Chuỗi ký tự'; // Khai báo biến chuỗi
	double  d     = 1.1234;        // Khai báo biến số thực
	int     i     = 1;             // Biến số nguyên
	bool    found = true;          // Biến logic (boolean)
```

Trong trường hợp bạn sử dụng biến mà biến đó không xét đến kiểu (chấp nhận gán
vào nó nhiều loại kiểu) thì dùng từ khóa `dynamic`

```dart
	dynamic dyn = 123;             // Khởi tạo là số int
	dyn = "Dynamic";               // Gán chuỗi
	dyn = 1.12345;                 // Gán số double
```
**Giá trị mặc định (Default value)**

Nếu 1 `variable` không được khởi tạo, thì giá trị mặc định của chúng là `null`. Ngay
kể cả chúng là kiểu `int` thì nếu không tạo thì giá trị mặc định vẫn là `null`, vì
mọi thứ trong Dart đều là `object`.

```dart
	int lineCount; 
	assert(lineCount == null);
```

**Lưu ý:** Hàm `assert()` bị bỏ qua trong mã production. Trong quá trình phát
triển, `assert(condition)` đưa ra một ngoại lệ trừ khi điều kiện là đúng. Để biết
chi tiết, [xem Assert.](https://dart.dev/guides/language/language-tour#assert)

## **HẰNG SỐ - KHAI BÁO & SỬ DỤNG**

Hằng số lưu giá trị mà không thể thay đổi, sử dụng từ khóa `const` hoặc
`final` để tạo ra hằng số; thay cho `var` hoặc đi kèm cùng các `type` khác như
`int, String, double`...

### **Tạo hằng số const**

```dart
	const tên_hằng_số = biểu_thức_giá_trị;
//Ví dụ
	const day_0     = 'Sunday';
	const day_1     = 'Monday';
	const minutes   = 24 * 60;
```

Cách khai báo `const` như trên gọi là hằng số lúc biên dịch (compile-time),
giá trị của nó phải là cụ thể ngay lúc bạn viết code.

### **Tạo hằng số final**

Thực ra đây giống như khai báo biến, nhưng biến `final` chỉ được gán một lần
duy nhất, gán lần thứ 2 sẽ lỗi (trước khi sử dụng phải có 1 lần gán). Nó gọi là
hằng số lúc chạy (run-time), giá trị hằng số này có thể khác nhau mỗi lần chạy.

Cú pháp như sau:

```dart
	final name_1          = biểu_thức_giá_trị;
	final String name_2   = biểu_thức_giá_trị;    //Chỉ rõ luôn kiểu của hằng
```

Xét 1 chương trình mẫu sau:

```dart
	var number_rand = Random(1000).nextInt(500);
//Tạo hằng số final
	final a = number_rand * 2;
```

Như ví dụ trên, tạo ra hàng số a. Hằng số này sau khi khởi tạo thì không thay
đổi nữa. Vấn đề hằng số này được khởi tạo bằng một giá trị ngẫu nhiên sinh ra
bởi hàm Random, vậy mỗi lần chạy ứng dụng hằng số này có thể có giá trị khác
nhau. Nó khác với `const` là cố định ngay từ khi viết code (hằng số biên
dịch).

Ví dụ sau sẽ bị lỗi:

```dart
	var number_rand = Random(1000).nextInt(500);
	const a = number_rand * 2;
--Kết quả: test.dart:7:13: Error: Not a constant expression.
```

Lỗi vì bạn không thể biết a bằng bao nhiêu khi đọc code

## **CÁC KIỂU DỮ LIỆU TRONG DART**

Dart đang hỗ trợ các nhóm kiểu dữ liệu:` Number `(Số), `String `(Chuỗi), `Logic`
(Đúng/Sai), `Symbol` (Biểu tượng), `Runes` (Chuỗi Unicode 32-bit).

### **Numbers (Số)**

Các kiểu số trong Dart tồn tại dưới 2 dạng chính:
[`int`](https://api.dart.dev/dev/2.8.0-dev.10.0/dart-core/int-class.html) và
[`double`](https://api.dart.dev/dev/2.8.0-dev.10.0/dart-core/double-class.html).

Cả int và double đều là subtypes của
[`num`](https://api.dart.dev/dev/2.8.0-dev.10.0/dart-core/num-class.html). Do
chúng đều là object nên có khá nhiều method hỗ trợ như `abs()`, `ceil()` làm tròn
lên, `floor()` làm tròn xuống. Nếu bạn muốn nhiều hơn thư viện `dart:math` có thể
giúp bạn.

```dart
	int x = 1; 
	int hex = 0xDEADBEEF; 
	double y = 1.1; 
	double exponents = 1.42e5;
	num z = 3.6; 			//Tự nhận kiểu double (num đại diện cho number)
```

Dưới đây là cách bạn chuyển từ `String` sang `Number` ngược lại:

```dart
//String -> int 
	var one = int.parse('1'); 
	assert(one == 1); 
// String -> double 
	var onePointOne = double.parse('1.1'); 
	assert(onePointOne == 1.1); 
// int -> String 
	String oneAsString = 1.toString(); 
	assert(oneAsString == '1'); 
// double -> String 
	String piAsString = 3.14159.toStringAsFixed(2); 
	assert(piAsString == '3.14');
```

### **String (Chuỗi)**

```dart
	var s1 = 'Single quotes work well for string literals.'; 
	var s2 = "Double quotes work just as well."; 
```

Để tạo 1 `String`, bạn có thể dụng nháy đơn `'` hoặc nháy kéo `"`. Đặc biệt, bạn có
thể truyền `value` (giá trị) vào trong `String` rất đơn giản `\$variable` (tên biến)
hoặc `\${expression}` (biểu thức):

```dart
String s1 = "Bui Phu Khuyen"; 
	String s2 = "Dart"; 
	print("$s1"); 
	print("${s1 + '_' + s2.toUpperCase()}"); 

--Kết quả:        Bui Phu Khuyen                                                           
                  Bui Phu Khuyen_DART                                     
```

Muốn nhập chuỗi trên nhiều dòng, dùng cú pháp sau (các dòng nằm giữa cặp `'''`
hoặc `"""`);

```dart
	var s1 = '''You can create
		multi-line strings like this one.''';
	var s2 = """This is also a 
	multi-line string.""";

--Kết quả:          
      	You can create                            
       	multi-line strings like this one.      
	This is also a           
	multi-line string.                 
```

Bạn có thể tạo `"raw"` string bằng cách thêm đằng trước **r**:

```dart
	var s = r"In a raw string, even \n isn't special.";
```
**_Chú thích_:** `Raw String` bạn có thể hiểu là nó sẽ hiển thị đúng như những gì bạn ghi lên, giả sử như đoạn code trên `\n` sẽ không được coi là xuống dòng nữa.

### **Bool (Đúng/Sai)**

Biểu diễn logic đúng / sai với hai giá trị `true`và `false`.

```dart
	bool found = true;
	if (found) {
	    //Do something
	}
```
### **Runes (Chuỗi Unicode 32-bit)**

Trong Dart, rune là các điểm mã UTF-32 của một chuỗi. Unicode xác định một giá
trị số duy nhất cho mỗi chữ cái, chữ số và ký hiệu được sử dụng trong tất cả các
hệ thống chữ viết của thế giới. Bởi vì chuỗi Dart là một chuỗi các đơn vị mã
UTF-16, việc thể hiện các giá trị Unicode 32 bit trong một chuỗi đòi hỏi cú pháp
đặc biệt. 

Cách thông thường để thể hiện điểm mã Unicode là `\\uXXXX`, trong đó
`XXXX` là giá trị thập lục phân 4 chữ số. Ví dụ: Ký tự trái tim ♥ là `\\u2665`. 

Để chỉ định nhiều hơn hoặc ít hơn 4 chữ số hex, đặt giá trị trong dấu ngoặc nhọn.
Ví dụ: Biểu tượng cảm xúc cười 😆 là `\\u{1f600}` .

Ta xem một chương trình minh hoạ sau:

```dart
	Runes input = Runes( '\u2665 \u{1f605} \u{1f60e} \u{1f47b}'); 
	print(String.fromCharCodes(input));
```

Kết quả của chương trình là:

> ♥  😅  😎  👻

### **Symbol (Biểu tượng)**

Một đối tượng Biểu tượng đại diện cho một toán tử hoặc mã định danh được khai báo trong chương trình Dart. Bạn có thể không bao giờ cần sử dụng các ký hiệu, nhưng chúng là vô giá đối với các API tham chiếu đến các mã định danh theo tên, bởi vì thu nhỏ thay đổi tên định danh nhưng không phải là ký hiệu định danh.

Để lấy ký hiệu cho mã định danh, hãy sử dụng ký hiệu bằng chữ, chỉ `#` theo sau là mã định danh:

```dart
	#radix
	#bar
```

Biểu tượng chữ là hằng số thời gian biên dịch. Bạn có thể xem thêm thông tin về
Symbol [tại đây](https://dart.dev/guides/language/language-tour#symbols).

