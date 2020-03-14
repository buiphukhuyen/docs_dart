

# **BÀI 2: LÀM QUEN VỚI NGÔN NGỮ DART (Phần 2)**

Ở phần 1 bài trước, ta đã tìm hiểu sơ qua 1 số khái niệm về từ khoá, biến, hằng
số và các kiểu dữ liệu trong Dart. Trong phần tiếp theo, ta cần biết một số nội
dung sau:

-   Toán tử? (Số học, Gán, So sánh, Logic, Biểu thức Điều kiện,…)

-   Câu điều kiện, vòng lặp trong Dart?

-   Hàm trong Dart?

-   Cấu trúc dữ liệu thường dùng (Enum, Interable, List, Set, Map)?

## **TOÁN TỬ**

### **Toán tử số học**

| **Toán tử**    | **Ý nghĩa**                                                                        |
|----------------|------------------------------------------------------------------------------------|
| **+**          | Phép cộng. 5 + 6 kết quả 11                                                        |
| **-**          | Phép trừ. 5 - 6 kết quả -1                                                         |
| **\***         | Phép nhân                                                                          |
| **/**          | Phép chia. 5 / 6 kết quả 0.8333333333333334                                        |
| **\~/**        | Phép chia lấy phần nguyên. 6 \~/ 4 kết quả 1                                       |
| **%**          | Phép chia modulo (lấy phần dư) 6 % 4 kết quả 2                                     |
| **-biểu_thức** | Đổi dấu kết quả biểu thức -(5 - 6) kết quả 1                                       |
| **++var**      | var = var + 1. Thêm 1 vào var, trong biểu thức việc tăng này được thực hiện trước.|
| **var++**      | var = var + 1. Thêm 1 vào var, trong biểu thức việc tăng này được thực hiện sau.   |
| **--var**      | var = var - 1. Bớt var đi 1, việc bớt này thực hiện trước trong biểu thức.         |
| **var--**      | var = var - 1. Bớt var đi 1, việc bớt này thực hiện sau trong biểu thức.           |


###  **Phép gán**

Phép gán là `=`, để thực hiện gán giá trị biểu thức bên phải vào biến ở phía bên
trái toán tử.

```dart
					biến = biểu_thức;
	var a = 1 + 2 + 3 + 4; //Gán phép toán cho biến a
```


Phép toán gán có trường hợp viết phức tạp kết hợp cùng một toán tử khác phía
trước dạng `toán_tử_trước=` như `+=, -=, *=, /*` ... Điều này có nghĩa là
biến và biểu thức bên phải thực hiện toán tử phía trước, giá trị được bao nhiêu
gán vào biến.

```dart
	a *= 5;   // Tương đương a = a * 5;
	a += 5;   // Tương đương a = a + 5;
	a /=  5;  // Tương đương a = a / 5;
```

### **Toán tử so sánh**

Các toán tử này thực hiện trên biểu thức `logic`, kết quả là `true` hoặc
`false`

| **Toán tử** | **Ý nghĩa**                                               |
|-------------|-----------------------------------------------------------|
| ==          | So sánh bằng 5 == 5 kết quả true, 5 == 6 kết quả false    |
| !=          | So sánh khác 5 != 5 kết quả false, 5 != 6 kết quả true    |
| \>          | So sánh lớn hơn 5 \> 5 kết quả false, 6 \> 5 kết quả true |
| \<          | So sánh nhỏ hơn 5 \< 5 kết quả false, 5 \< 6 kết quả true |
| \<=         | So sánh nhỏ hơn hoặc bằng                                 |
| \>=         | So sánh lớn hơn hoặc bằng                                 |

###  **Toán tử logic**

| **Toán tử** | **Ý nghĩa**                                                       |
|-------------|-------------------------------------------------------------------|
| \|\|        | Phép logic **hoặc**, a\|\|b kết quả true nếu a hoặc b là true     |
| &&          | Phép logic **và**, a&&b kết quả true nếu a và b đều true          |
| !biểu_thức  | Phép **phủ định** !a nếu a là true thì kết quả phép toán là false |

###  **Biểu thức điều kiện**

**`biểu_thức_điều_kiện ? biểu_thức_1 : biểu_thức_2`**

Biểu thức tổng hợp trên kết hợp từ ba biểu thức con (còn được gọi với cái tên
khác là toán tử ba ngôi). Nếu `biểu_thức_điều_kiện` là `đúng` thì giá trị
tính theo `biểu_thức_1`, ngược lại là `biểu_thức_2`.

```dart
	var a = 5;
	var b = 10;
	var c = (a > b) ? a : b; //Kết quả c = 10
```

**`biểu_thức_1 ?? biểu_thức_2`**

Biểu thức kết hợp với `??`, nếu `biểu_thức_1` **khác** `null` thì lấy
`biểu_thức_1`, ngược lại lấy giá trị từ `biểu_thức_2`.

```dart
	var a = 5;
	var b;
	var c = a ?? b; //Kết quả c = 5
```

### **Một số toán thử trên lớp, đối tượng**

| **Toán tử** | **Ý nghĩa**                                                                               |
|-------------|-------------------------------------------------------------------------------------------|
| **[]**      | Truy cập phần tử mảng                                                                     |
| **.**       | Truy cập phương thức, thuộc tính đối tượng                                                |
| **?.**      | Truy cập phương thức, thuộc tính đối tượng khi đối tượng đó khác null myobject?.method(); |
| **as**      | Chuyển kiểu: (var as MyClass)                                                             |
| **is**      | Kiểm tra kiểu: (var is MyClass)                                                           |
| **is!**     | Kiểm tra kiểu: (var is! MyClass)                                                          |
| **..**      | Thực hiện chuỗi hoạt động trên cùng một đối tượng                                         |

## **CÂU ĐIỀU KIỆN, VÒNG LẶP**

### **Câu lệnh IF - ELSE**

Dạng 1, thực hiện khối lệnh khi biểu thức `logic` kiểm tra là `true`:

```dart
	if (biểu_thức) {
    		//Viết lệnh chạy khi biểu_thức là true
	}
```
Dạng 2, nếu điều kiện là `true` thực hiện khối lệnh 1, nếu `false` thực hiện khối lệnh
2.

```dart
	if (biểu_thức) {
    		//Viết lệnh chạy khi biểu_thức là true
	} else {
    		//Viết lệnh chạy khi biểu thức là false
	}
//CÓ THỂ VIẾT NHIỀU LỆNH IF
	if (biểu_thức_1) {
    		//..Các câu lệnh
	} else if (biểu_thức_2) {
    		//Các câu lệnh
	} else if (biểu_thức_3) {
    		//Các câu lệnh
	} else {
    		//Các câu lệnh
	}
```
Ví dụ:

```dart
var a = 15;
	if (a < 10) {
    		print('a nhỏ hơn 10');
	} else if (a < 5) {
    		print('a nhỏ hơn 5');
	}
	else {
    		print('a lớn hơn hoặc bằng 15');
	}
```
### **Câu lệnh rẽ nhánh SWITCH**

Khi cần rẽ nhiều nhánh, thay vì dùng nhiều lệnh `if else` ở trên thì có thể
dùng `switch` với cú pháp.

```dart
	switch (biểu_thức) {
    		case : giá_trị_1
      			// Khối lệnh
      			break;
    		case : giá_trị_2
      			//Khối lệnh
      			break;
    		default :
      			//Khối lệnh mặc định
}
```

Giá trị của `biểu_thức` được so sánh với các giá trị `giá_trị_1`, `giá_trị_2`
... nếu bằng cái nào thì thi hành khối lệnh bắt đầu tử điểm đó cho đến khi gặp
`break;`

Nếu có khối `default` thì khi không có giá trị nào phù hợp sẽ thi hành khối
này.

```dart
var t = 1;
	switch(t) {
    		case 0:
      			print('Bui'); break;
    		case 1:
      			print('Phu'); break;
    		default:
      			print('Khuyen');
} 
//Kết quả: Phu
```

### **Vòng lặp FOR**

Cú pháp:

```dart
for (statement1; statement2; statement3) {
   	 	//Khối lệnh thi hành
	}
```

-   **`statement1`** lệnh thi hành trước khi vòng lặp `for` bắt đầu.

-   **`statement2`** điều kiện kiểm tra trước mỗi lần thi hành khối lệnh `for`
    (`true` thì khối lệnh sẽ thi hành, `false` sẽ khối `for` sẽ không thi hành
    - thoát lặp).

-   **`statement3`** thi hành sau mỗi lần một vòng hoàn thành.

Ví dụ:

```dart
	for (var i=1; i<=5; i++) {
    		print(i);
	}
//Kết quả
    1
    2
    3
    4
    5
```

Có thể bỏ qua `statement1` (vẫn giữ lại dấu `;`)

```dart
	var i = 1;
	for (; i<=5; i++) {
    		print(i);
	}
```
Tương tự bạn có thể bỏ qua `statement3` và `statement2` (vẫn giữ `;`), lưu
ý bạn cũng có thể sử dụng lệnh `break;` để thoát vòng lặp.

```dart
	var i = 0;
	for (; ; i+=2) {
  		if (k>10) break;
  		print(k);
	}
//Kết quả
    2
    4
    6
    8
```

###  **Vòng lặp WHILE**

Thi hành khối lệnh khi mà điều kiện kiểm tra vẫn là `true`

```dart
	while (điều_kiện) {
   		//Khối lệnh
	}
```

Đầu tiên nó kiểm tra điều kiện, nếu `true` sẽ thi hành khối lệnh. Đến cuối
khối lại kiểm tra điều kiện, nếu điều kiện vẫn là `true` thì lại tiếp tục thì
hành vòng mới của khối lệnh. Ví dụ:

```dart
	var i = 0;
	while (i<=5) {
    		print(i);
    		i++;
	}
//Kết quả
    0
    1
    2
    3
    4
    5
```
Lưu ý về việc sau một số vòng thì điều kiện phải là `false` nếu không vòng lặp
sẽ lặp lại vô tận.

### **Vòng lặp DO WHILE:**

Giống với vòng lặp **`while`** nhưng khối lệnh thi hành luôn mà không kiểm tra
điều kiện trước, khi khối lệnh thi hành xong mới kiểm tra điều kiện để xem có
lặp lại hay không. Cú pháp như sau:

```dart
do {
   		//Khối lệnh
	}
	while (condition);
```	
Ví dụ:

```dart
	var i = 10;
	do {
    		print(i);
    		i++;
	}
	while (i<=15);
//Kết quả
    10
    11
    12
    13
    14
    15
```

Lưu ý: Vòng lặp **`do ... while`** khối lệnh luôn được thi hành ít nhất một lần.

### **Lệnh continue và break**

Trong vòng lặp khi gặp **`continue;`** nó sẽ bỏ qua các lệnh còn lại và khởi tạo
vòng lặp mới luôn. Còn nếu gặp **`break;`** thì bỏ qua các lệnh còn lại đồng thời
thoát khỏi vòng lặp. Ví dụ:

```dart
	for (i = 1; i <= 1000; i++) {
   		if (i == 5) {
      			continue;          //Khởi tạo vòng lặp mới luôn
   		}
   	    	print(i);
   		if (i > 6) {
        		break;             //Thoát vòng lặp nếu i > 6
    		}
	}
//Kết quả (Bỏ qua in số 5)
    1
    2
    3
    4
    6
    7
```

Lệnh **`continue`** còn dùng để nhảy đến một khối lệnh có nhãn bằng cú pháp:

```dart
  		continue  nhãn_khối_lệnh;
```
Lệnh **`break`** còn dùng để hủy thi hành khối lệnh bên ngoài có nhãn, với cú
pháp:

```dart
		break nhãn_khối_lệnh_ngoài;
```
Phần nói về các đối tượng có kiểu liệt kê được (Ví dụ như mảng, danh sách ...),
còn có các lệnh duyệt qua từng phần tử liệt kê được đó với các lệnh `for ...
in, for ... of.`

###  **Test với Assert**

Dart cung cấp lệnh:

```dart
  		Assert(biểu_thức_logic);
```
Để khi chạy mà biểu thức logic sai sẽ dừng chương trình ở đó. **`Assert`** là cách
để kiểm tra một biểu thức, vấn đề là nó không có ảnh hưởng gì khi chạy ở chế độ
product nó chỉ tác dụng khi phát triển (Chạy debug Ctrl + F5 trong VS)

```dart
	// Đảm bảo một đối tượng khác null
		assert(myobject != null);

	// Đảm bảo số lớn hơn 100
		sassert(number > 100);
```

## **XÂY DỰNG HÀM**

### **Hàm trong Dart**

Hàm là một khối lệnh thực hiện một tác vụ gì đó, khối lệnh này được dùng nhiều
lần nên gom chúng tại thành một hàm. Trong Dart mọi thứ đều là đối tượng nên hàm
cũng là một đối tượng (kế thừa `Function`). Đây là một khai báo hàm:

```dart
	double Sum(double a, double b, double c) {
  		return a + b + c;
	}
//Gọi hàm
	var x = Sum(1, 2, 3);
	print(x); 
//Kết quả 6.0
```

Như vậy khi khai báo hàm ta có thể có các thành phần sau:

-   Chỉ ra kiểu giá trị trả về của hàm (ví dụ `double`), giá trị trả về bằng
    biểu thức của lệnh `return`. Với Dart thiếu việc khai báo kiểu giá trị trả
    về hàm vẫn hoạt động tốt. Còn khi có chỉ rõ kiểu trả về thì giá trị trong
    biểu thức `return` phải trùng với kiểu khai báo hàm.

-   Tham số được liệt kê sau tên hàm trong cặp **`()`** như trên có ba tham số
    `a, b, c`.

-   Hàm kết thúc khi chạy hết khối lệnh hoặc gặp lệnh `return`, giá trị hàm là
    biểu thức sau `return`, nếu thiếu giá trị hàm sẽ là `null`.

-   Gọi hàm thì viết tên hàm và truyền đúng tham số theo thứ tự khi khai báo.

### **Hàm với tên tham số tuỳ chọn (Optional named parameters)**

Khi gọi 1 hàm (`function`), bạn có truyền giá trị thông qua tên biến
**`paramName: value`**, việc này giúp việc đọc code dễ dàng hơn trong các trường
hợp hàm (`function`) có quá nhiều tham số (`parameter`).

Để làm được thế, hàm phải khai báo tham số ở trong **`{ }`**, Ví dụ: **`{param1,
param2,…}`**

```dart
	String Label( {String surName, String midName, String frsName }) {
  		return surName + midName + frsName;
	}
	var result = Label(surName: 'Bui ', midName: 'Phu ', frsName: 'Khuyen ');
	print(result);  //Bui Phu Khuyen
```

### **Hàm với tham số tuỳ chọn (Optional positional parameters)**

Các tham số tùy chọn của hàm có nghĩa là khi họi hàm có sử dụng hoặc không. Các
tham số tùy chọn gom lại trong **`[ ]`**, nếu khi gọi hàm không có tham số này thì
nó nhận giá trị `null`

```dart
double Sum(double a, [double b, double c]) {
   		var result = a;
   		if (b != null)
    			result += b;
   		result += (c!=null) ?  c: 0;
		return result;
	}
	print(Sum(1));       //1.0
	print(Sum(1,2));     //3.0;
	print(Sum(1,2,3));   //6.0;
```

### **Giá trị tham số mặc định của hàm (Default parameter values)**

Giá trị tham số mặc định của hàm (Default parameter values) được sử dụng nếu bạn
muốn tham số có giá trị mặc định, nghĩa là khi gọi hàm mà thiếu giá trị cho tham
số đó, thì nó sẽ nhận mặc định. Ví dụ:

```dart
double Sum(double a, {double b=1, double c=2}) {
  		return a + b + c;
	}
	var result_1 = Sum(1);
	print(result_1);  //4.0
	var result_2 = Sum(1, c:10);
	print(result_2);  //12.0
	var result_3 = Sum(1, c:2, b:10);
	print(result_3);  //13.0
```

Hàm trên tham số b mặc định là 1, c mặc định là 2. Nếu không chỉ ra tham số này
khi gọi nó sẽ dùng mặc định, còn muốn chỉ ra khi gọi thì truyền theo cú pháp
`tên_tham_số:giá_trị`, như ví dụ trên: `tinhtong(1, c:2, b:10)`

###  **Hàm với Ký hiệu mũi tên =\> (=\> expression)**

Với những hàm **chỉ có một** biểu thức (expression) trả về luôn, thì có thể có cách viết ngắn gọn bằng ký hiệu mũi tên:

```dart
double Sum(var a, var b) {
    		return a + b;
  	}

// Có thể viết lại thành
  	double Sum(var a, var b) => a + b;
```

Nghĩa là: `=> expression` là cách viết gọn của `{ return expression; }`

**Lưu ý:** Chỉ có biểu thức (`expression`) đứng đằng sau `=>`, không áp dụng cho
câu lệnh (`statement`).

Ví dụ: Bạn **không thể** để `if statement` đằng sau `=>` được. Tuy nhiên bạn có thể sử
dụng toán tử ba ngôi:

```dart
   			condition ? expr1 : expr2
```
## **CẤU TRÚC DỮ LIỆU THƯỜNG DÙNG**
### **Cấu trúc dữ liệu liệt kê Enum**

Trong Dart đây là một loại lớp đặc biệt, biểu diễn một tập hợp cố định các hằng số. Để tạo ra một `enum` dùng từ khóa `enum` khai báo các phần tử liệt kê theo tên cách nhau bởi `,` Ví dụ:

```dart
var user_group = UserGroup.admin;
	switch (user_group) {
    		case UserGroup.admin:
      			print('Quản trị hệ thống');
    			break;
    		case UserGroup.guest:
      			print('Khách');
    			break;
    		default:
			print('Thành viên');
	}
//Kết quả: Quản trị hệ thống
```

### **Cấu trúc dữ liệu Iterable**

`Iterable` là một lớp generic biểu diễn tập hợp dữ liệu mà có thể duyệt qua hết
phần tử này đến phần tử khác. Nghĩa là nó hỗ trợ `moveNext()` để đi đến phần tử
tiếp theo, lấy dữ liệu phần tử hiện tại bằng `iterator.current`.

Thường thì `Iterable` được tạo ra, liên kết với một loại kiểu dữ liệu tập hợp khác
như List, Map... Xem các loại cấu trúc dữ liệu này để tìm hiểu về `Interable`

Duyệt qua các phần tử `Iterable`:

```dart
//Sinh ra Iterable chứa 100 phần tử số từ 0 - đến 99
	var iterable = Iterable.generate(100);
	for (var item in iterable) {
   	 	print(item);
	}
//Kết quả: 	0
		1
	       ...
		99
```

Hoặc duyệt qua bằng forEach:

```dart
	iterable.forEach((item) {
    		print(item);
	});
```

**Các phương thức / thuộc tính hay dùng trên mảng - danh sách:** [(Xem
thêm)](https://api.dart.dev/stable/2.7.1/dart-core/Iterable-class.html)

| **Phương thức** | **Sử dụng**                                                                |
|-----------------|----------------------------------------------------------------------------|
| **isEmpty**     | Thuộc tính kiểm tra xem mảng rỗng                                          |
| **isNotEmpty**  | Thuộc tính kiểm tra xem mảng không rỗng                                    |
| **length**      | Thuộc tính trả về số lượng phần tử mảng                                    |
| **first**       | Thuộc tính trả về phần tử đầu tiên, tương đương với [0], lỗi nếu mảng rỗng |
| **last**        | Thuộc tính trả về phần tử đầu cuối                                         |
| **forEach()**   | Duyệt qua các phần tử                                                      |

###  **Cấu trúc dữ liệu Danh sách – Mảng – LIST**

 Trong Dart, danh sách (cũng là mảng) được định nghĩa từ lớp `generic List`, nó chứa một tập hợp các dữ liệu - mỗi dữ liệu trong `List` là gọi là phần tử, vị trí của nó xác định bằng chỉ số bắt đầu từ 0, truy cập đến mảng (danh sách) dùng ký hiệu `[]` chứa chỉ số phần tử. Có 2 loại `List`, đó là loại mà số phần tử có thể thay đổi và loại `list` có số phần tử cố định:

 **Khởi tạo một mảng cố định**

```dart
//Khai báo mảng cố định 2 phần tử
	var listState = List(2);
//Khởi tạo các phần tử trong mảng
	listState[0] = 'on';
	listState[1] = 'off';
//Nếu truy cập listState[2] sẽ lỗi - vì List chỉ có 2 phần tử
	print(listState); 	//[on, off]
```

 **Khởi tạo một mảng thay đổi số phần tử được**

Nếu khi khởi tạo mà không chỉ ra số lượng phần tử thì nó là mảng thay đổi số
phần tử được, lúc này có thể áp dụng các hàm thêm, bớt phần tử sẽ nói phía dưới:

```dart
//Khai báo mảng thay đổi được
	var day = List();
//Thêm các phần tử vào mảng
	day.add('Monday');
	day.add('Tuesday');
	day.add('Thursday');
	print(day);             //[Monday, Tuesday, Thursday]
//Xóa phần tử cuối cùng
	day.removeLast();
	print(day);             //[Monday, Tuesday]
```

Nếu muốn tạo ra mảng thay đổi được, và khởi tạo luôn dữ liệu ở phần khai báo thì
dùng ký hiệu **`[]`**

```dart
//Khởi tạo mảng với 2 phần tử
	var group = ['member', 'admin'];
	group.insert(0, 'guest'); 		//Chèn phần tử vào vị trí 0
	print(group);             		//[guest, member, admin]
```

**Các phương thức / thuộc tính hay dùng trên mảng - danh sách** [(Xem
thêm)](https://api.dart.dev/stable/2.7.1/dart-core/List-class.html)

Ngoài các phương thức - thuộc tính giống như [**`Iterable`**](#cấu-trúc-dữ-liệu-iterable) chú ý thêm:

| **Phương thức**   | **Sử dụng**                                                                     |
|-------------------|---------------------------------------------------------------------------------|
| **reversed**      | Trả về một đối tượng Iterable chứa các phần tử mảng theo thứ tứ ngược lại (đảo) |
| **add()**         | Thêm một phần tử vào cuối add(element)                                          |
| **insert()**      | Chèn một phần tử vào mảng ở vị trí i insert(i,element)                          |
| **insertAll()**   | Chèn một một Iterable bắt đầu từ vị trí i: insertAll(i,iterable)                |
| **remove()**      | Xóa bỏ phần tử đầu tiên tìm thấy có giá trị chỉ ra remove(data)                 |
| **removeAt()**    | Xóa bỏ phần tử ở vị trí i removeAt(i)                                           |
| **removeLast()**  | Xóa bỏ phần tử cuối                                                             |
| **removeRange()** | Xóa bỏ phần tử từ vị trí start đến vị trí end removeRange(start, end)           |

### **Cấu trúc dữ liệu Ánh xạ - MAP**

Đây là kiểu tập hợp dữ liệu mà mỗi phần tử biểu diễn theo cặp **`key:value`**

Các phần tử của `Map` được truy cập bằng ký hiệu `[]` chứa `key` dạng `map[key]`

Khởi tạo `Map` có thể dùng `Contructors` hoặc khởi tạo luôn một số phần tử bằng `{ }`

```dart
//Tạo một map, khới tạo luôn 3 key - name, age, score
  	var student = {
    		'name':'Bui Phu Khuyen',
    		'age': 22,
    		'score': 'A'
  	};
  	student['subject'] = 'Dart Language'; 	//Thêm một phần tử
  	print(student['name']);      		 	//Truy cập phần tử
	print(student['subject']);    		
//Kết quả:
	Bui Phu Khuyen
	Dart Language
```

Cũng hoàn toàn tạo ra `Map` từ `Contructors Map()`:

```dart
	var student = Map();
  	student['name']   = 'Bui Phu Khuyen';
  	student['age']    = 22;
  	student['score']  = 'A';
//Duyệt qua các phần tử (cách 1)
  	student.forEach((key, value) {
    		print('$key : $value');
  	});
//Duyệt qua tất cả các phần tử Map (cách 2)
  	for (var key in student.keys) {
    		print('$key :  ${student[key]}');
  	}
```

**Các phương thức / thuộc tính hay dùng trên Map** [(Xem
thêm)](https://api.dart.dev/stable/2.7.1/dart-core/Map-class.html)

Ngoài các phương thức - thuộc tính giống như [**`Iterable`**](#cấu-trúc-dữ-liệu-iterable) chú ý thêm:

| **Phương thức**   | **Sử dụng**                                        |
|-------------------|----------------------------------------------------|
| **addAll()**      | Thêm các phần tử từ một Map khác addAll(other_map) |
| **clear()**       | Làm rỗng Map clear();                              |
| **containsKey()** | containsKey(key) kiểm tra phần tử với key tồn tại  |
| **remove()**      | remove(key) xóa phần tử khỏi Map                   |

### **Cấu trúc dữ liệu Tập hợp – SET**

Tập hợp như tên gọi là là tập hợp các phần tử, đảm bảo sao cho mỗi phần tử chỉ
được xuất hiện 1 lần.

Khởi tạo một tập hợp bằng `Contructors` với cú pháp:

```dart
			var elements = Set();
```

Hoặc có thể khởi tạo luôn một số phần tử bằng `{ }`

```dart
			var halogens = {'chlorine', 'bromine', 'iodine', 'astatine'};
```

**Các phương thức / thuộc tính hay dùng trên Set** [(Xem
thêm)](https://api.dart.dev/stable/2.7.1/dart-core/Set-class.html)

Nó có các phương thức và cách duyệt qua phần tử giống phần trình bày
[**Iterable**](#cấu-trúc-dữ-liệu-iterable) ở trên.

Để thêm một phần tử vào tập hợp dùng hàm `add(ele);`, để loại bỏ phần tử dùng hàm
`remove(ele);`, kiểm tra xem có chứa phần tử bằng hàm `contains(ele);`...

```dart
var halogens = {'chlorine', 'bromine'}; //Khởi tạo Set bằng {}
	var elements = Set();  	//Khởi tạo Set bằng Contructors
	elements.add('fluorine'); 	//Thêm phần tử vào elements
	elements.add('chlorine'); (1)  //Thêm phần tử vào elements
	elements.addAll(halogens);(2)	//Thêm các phần từ halogens vào elements
	print(elements);
//Kết quả: 	{fluorine, chlorine, bromine}
//Giải thích: Vì Set elements đã thêm phần tử 'chlorine' ở dòng lệnh (1) nên khi qua lệnh (2) chỉ lấy thêm phần tử 'bromine' trong Set halogens (Đảm bảo tính chất của Tập hợp Set – đảm bảo phần tử chỉ xuất hiện 1 lần)
```
