# **BÀI 3: LẬP TRÌNH HƯỚNG ĐỐI TƯỢNG TRÊN DART**

Ở các bài bài trước, ta đã tìm hiểu sơ qua 1 số khái niệm và các kỹ thuật cơ bản
của lập trình Cấu trúc trong Dart. Trong bài này, chúng ta sẽ đi qua 1 phần khá
quan trọng trong nội dung cả chương: “Lập trình hướng đối tượng OOP”, nội dung
của bài này sẽ gồm các phần sau:

-   Object? Class? Cách tạo 1 Class?

-   Các loại phương thức khởi tạo?

-   Tính kế thừa trong lớp? Lớp trừu tượng?

-   Một số lưu ý bổ sung về Class?

## **CLASS**

Class để tạo ra các đối tượng, với Dart mọi thứ kể cả số đều là đối tượng, các
đối tượng đề kế thừa từ class Object

Trong một class nó có thể có các thành phần:

-   Các phương thức khởi tạo - Hàm được gọi khi tạo ra một đối tượng mới từ
    class.

-   Các biến lưu dữ liệu của đối tượng - gọi là các trường - các thuộc tính.

-   Các hàm - gọi là các thành viên hàm - các phương thức.

-   Các hàm đặc biệt gọi khi thực hiện gán thuộc tính / truy cập thuộc tính -
    hàm setter/getter.

Từ lớp đã có khởi tạo đối tượng bằng cách gọi hàm khởi tạo của nó, sau khi có
đối tượng thì truy cập vào các thành viên (phương thức, thuộc tính) bằng ký hiệu
chấm . như object.phuongthuc();

Khai báo một lớp thì dùng từ khóa class, ví dụ sau khai báo một lớp:

```dart
   class Product {
	  	//Khai báo các thuộc tính
	  	String manufacture = '';
	  	String name = '';
	  	var    price;
	  	int    quantity;
	  	//Khai báo hàm khởi tạo (có tham số)
	  	Product(var price, {int quantity=0}) {
	   	   this.price    = price;
	    	   this.quantity = quantity;
	  	}
	  	//Khai báo phương thức Tính tổng giá
	  	calulateTotal() {
	    	   return this.price * this.quantity;
	  	}
	  	//Khai báo phương thức Hiển thị tổng giá
	  	showTotal() {
	    	   var total = this.calulateTotal();
	    	   print("Total Price is: $total");
  		}
   }
```

Sử dụng:

```dart
//Khởi tạo đối tượng product với 2 tham số truyền vào là price và quantity
   var product = Product(600, quantity: 1);
   product.showTotal();
//Thay đổi giá trị quantity
   product.quantity = 2;
   product.showTotal();

//Kết quả:
   Total Price is: 600
   Total Price is: 1200
```

Như vậy ta thấy **khai báo thuộc tính, phương thức** trong lớp tương tự như khai
báo biến và hàm thông thường chỉ có điều nó nằm trong class.

Để truy cập vào một phương thức, thuộc tính dùng ký kiệu chấm **`.`** Ví dụ:
`product.quantity = 2`, `product.showTotal()`

Trong phương thức của lớp, để tham khảo đến đối tượng của lớp dùng từ khóa
**`this`**, Ví dụ trong phương thức `calulateTotal()` có đoạn `return this.price *
this.quantity;`

Khi đã có lớp, việc tạo ra đối tượng lớp thì dùng toán tử **`new`**, `var product =
new Product(600, quantity: 1)` hoặc **không cần** toán tử **`new`** vẫn được chấp nhận
`product = Product(600, quantity: 1)` (\*)

> **Chú thích (\*):** Đối với Dart (phiên bản 2 trở đi), không bắt buộc dùng toán
> tử **new** khi khởi tạo 1 đối tượng (optional).

Khi khởi tạo như vậy, nó sẽ gọi đến phương thức có cùng tên với lớp, gọi là
phương thức khởi tạo - để thiết lập các thông tin cho lớp, ở ví dụ trên có một
phương thức khởi tạo `Product(var price, {int quantity:0})`, tuy nhiên bạn có thể
tạo ra nhiều phương tức khởi tạo có tên gọi theo nguyên tắc như sau:

### **Phương thức khởi tạo mặc định (Default Constructors)**

Nếu ta không tạo `Constructor` cho class (phương thức khởi tạo), mặc định Dart sẽ
tạo ra `Constructor` không tham số cho class đó.

Ví dụ:

```dart
   class Product {
	  	//Khai báo các thuộc tính
	  	String manufacture = '';
	  	String name = '';
	  	var    price;
	  	int    quantity;
	  	//Constructor mặc định – không tham số (Dart sẽ tự tạo ra)
	  	Product() {
		   print("Default Constructor");
	  	} 
	}
  // ...
  //Khởi tạo đối tượng
  var product = Product();
  //Kết quả: Default Constructor
```

### **Phương thức khởi tạo có định danh (Named Constructors)**

Đánh tên cho `Constructor` giúp cho `Constructor` có nghĩa và rõ ràng hơn. Giả sử ta sẽ tạo ra phương thức khởi tạo tên **iPhone** và **Samsung** để khởi tạo từng loại sản phẩm cụ thể, thì khai báo trong lớp như sau:

```dart
   class Product {
	  	// ...
	  	// Định danh Constructor iPhone
	  	Product.iPhone(var price, {int quantity=0}) {
	    	   this.price       = price;
	    	   this.quantity    = quantity;
	    	   this.manufacture = 'Apple';
	   }
	  	// Định danh Constructor Samsung
	  	Product.samsung(var price, {int quantity=0}) {
	    	   this.price       = price;
	    	   this.quantity    = quantity;
	    	   this.manufacture = 'Samsung';
	  	}
   }
```

Nếu vậy bạn có thể khởi tạo đối tượng `product` và `product2` bằng phương thức khởi
tạo này như sau:

```dart
var product = Product.iPhone(700, quantity: 1);
var product1 = Product.Samsung(600, quantity: 2);
```

Lúc này, tất cả các đối tượng khởi tạo bằng 2 phương thức này đều có thuộc tính
`manufacture` là `'Apple' (product)` hoặc `'Samsung' (product2)`.

### **Factory Constructors**

Đối với Phương thức khởi tạo này. Bạn có thể khởi tạo đối tượng tuỳ ý mà khi trả
về đối tượng thoả yêu bạn muốn dựa vào những điều kiện đi kèm, bằng cách sử dụng
từ khoá **`factory`** trước `Constructor`. Ví dụ:

```dart
   class Product {
	  	//...
	  	// Định danh Constructor iPhone
	  	Product.iPhone() {
	    	   print("Named Constructor iPhone!");
	  	}
	  	// Định danh Constructor Samsung
	  	Product.samsung() {
	   	   print("Named Constructor Samsung!");
	  	}
	  	// Định danh Constructor Other
	  	Product.other() {
	    	   print("Named Constructor Other!");
	  	}
	  	//Factory Constructor 
	  	factory Product(String manufacture) {
		   if(manufacture == 'Apple')
			return Product.iPhone();
		   else if(manufacture == 'Samsung')
			return Product.samsung();
		   else 
			return Product.other();
	  	} 
	}
  // ...
  //Khởi tạo đối tượng
  var product = Product('Samsung');
  //Kết quả: Named Constructor Samsung!
```
###  **Phương thức tĩnh (Static Constructors)**

Các phương thức (hàm) trong lớp chỉ truy cập được trên một đối tượng cụ thể
triển khai từ lớp (biến `product`), nhưng bạn có thể chỉ định phương thức là tĩnh
bằng từ khóa **`static`**, thì hàm không cần đối tượng triển khai từ lớp để hoạt
động mà có thể gọi hàm đó thông qua tên lớp. Ví dụ: Khai báo phương thức có tên
`showListStore()` là phương thức tĩnh.

```dart
   class Product {
	  	// ...
	  	static showListStore() {
	    	   print('Store 1 ...');
	    	   print('Store 2 ...');
	  	}
	  	// ...
   }
```

Như vậy bất kỳ đâu cũng có thể gọi đến phương thức này mà không cần khởi tạo đối
tượng. Chỉ cần tên lớp để gọi (cần nhớ là phương thức này thuộc về lớp chứ không
thuộc về đối tượng triển khai từ lớp).

```dart
 	Product.showListStore();
```
### **Phương thức Setter/Getter**

Ta có thể xây dựng hàm đặc biệt gọi mà có thể truy cập nó giống phương thức thì
nó thi hành (`Setter` gọi khi thực hiện gán, `Getter` gọi khi truy cập). Sử dụng từ
khóa `set` trước một hàm không có tham số thì hàm đó trở thành `Setter`, sử dụng từ
khóa `get` trước hàm 1 tham số thì đó là hàm `Getter`.

Ví dụ có thêm vào lớp `Product` hàm `Getter` và `Setter` đều có tên là `nameProduct`:

```dart
   class Product {
	  	// ...
	  	//Phương thức Getter
	  	get nameProduct {
	    	   return this.name;
	  	}  
	  	//Bạn có thể viết gọn thành: get nameProduct => this.name;
	  	//Phương thức Setter
	  	set nameProduct(name) {
	    	   this.name = name;
	    	   switch (this.name) {
	      		case 'IPhone 11 Pro Max':
	        	   this.manufacture = 'Apple';     break;
	      		case 'Galaxy Note 10':
	        	   this.manufacture = 'SamSung';   break;
	      		default: this.manufacture = '';
	    	   }
	  	}
  	// ...
   }
```

Sau khi có `Getter/Setter` thì truy cập giống như thuộc tính:

```dart
	product.nameProduct = 'Galaxy Note 10';  	//Gọi đến hàm Setter 
	var info = product.nameProduct;         	//Gọi đến Getter
```

## **TÍNH KẾ THỪA TRONG LỚP - EXTENDS**

Từ một lớp đã có, bạn có thể tạo ra một định nghĩa lớp mới, lớp mới đó gọi là
lớp kế thừa - lớp con luôn có các thuộc tính, phương thức từ lớp mà nó kế thừa
(gọi là lớp cha).

Để xây dựng một lớp mới kế thừa lớp đã có dùng tới từ khóa **`extends`**, Ví dụ từ lớp
`Product` xây dựng thêm lớp `Tablet` có thêm thuộc tính mô tả chiều dài, chiều rộng
của sản phẩm.

```dart
   class Product {
	  	//Khai báo các thuộc tính
	  	String manufacture = '';
	  	String name = '';
	  	var    price;
	  	int    quantity;
	  	//Khai báo hàm khởi tạo (có tham số)
	  	Product(var price, {int quantity=0}) {
	   	   this.price    = price;
	    	   this.quantity = quantity;
	  	}
	  	//Khai báo phương thức Tính tổng giá
	  	calulateTotal() {
	    	   return this.price * this.quantity;
	  	}
	  	//Khai báo phương thức Hiển thị tổng giá
	  	showTotal() {
	    	   var total = this.calulateTotal();
	    	   print("Total Price is: $total");
	  	}
   }
   class Tablet extends Product {
	  	double width    = 0;
	  	double height   = 0;
	  	Tablet(var price) : super(price, quantity:1) {
	    //Code khởi tạo tại lớp con, sau khi phương thức khởi tạo lớp cha chạy xong
	    	   this.name = "IPad Pro"; //Truy vấn được từ lớp cha
	  	}
   }
```

###  **Khởi tạo tại lớp con và sự truy vấn đến lớp cha**

Lớp con nói chung sẽ có những thuộc tính và phương thức kế thừa từ lớp cha, nên
từ lớp con bằng từ khóa **`this`** có thể truy cập đến những thành phần này. Tuy
nhiên có những phương thức mà lớp con sẽ định nghĩa lại mà vẫn giữ tên cũ (quá
tải) lúc này **`this`** sẽ sử dụng phương thức định nghĩa lại, tuy nhiên phiên bản
ở lớp cha vẫn còn đó, lúc này nếu muốn truy cập đến phiên bản định nghĩa bởi lớp
cha sẽ dùng ký hiệu **`super`** thay cho **`this`** (xem thêm phần quá tải hàm ở
dưới).

Phương thức khởi tạo ở lớp con, nói chung bắt buộc cũng phải gọi một phương thức
khởi tạo nào đó của lớp cha. Để làm được điều đó sau hàm khởi tạo của lớp con
chỉ rõ hàm tạo nào cả lớp cha sẽ gọi sau dấu **`:`**

Ở ví dụ trên chính là đoạn `super(price, quantity:1)` tương đương với hàm khởi tạo
`Product(price, quantity:1)`

Trở lại lớp Tablet trên, khi tạo đối tượng từ lớp:

```dart
var tablet = Tablet(500);
```

Phương thức khởi tạo thi hành nó đã gọi đến phương thức khởi tạo của lớp cha
`Product` rồi đến các code của chính Phương thức khởi tạo `Tablet`.

###  **Nạp chồng phương thức/ toán tử**

Bạn có thể tạo ra phiên bản mới của một phương thức đã có trên lớp cha và từ đây
đối tượng sẽ sử dụng phương thức mới được định nghĩa, để làm điều đó ở lớp con
tạo lại phương thức với chỉ thị được gọi là **`@override`** - nạp chồng phương
thức.

Ví dụ, ta sẽ nạp chồng phương thức `showTotal()`:

```dart
   class Tablet extends Product {
  	// ...
  	@override
  	showTotal() {
      	   print('Name Tablet is: ' + this.name);
      	   //Gọi đến phương thức ở lớp cha bằng từ khoá super
          super.showTotal();
    	}
 	// ...
   }
```

Ở phiên bản ở lớp con, do có nhu cầu sử dụng lại phương thức của lớp cha nên nó
có gọi đến phương thức cũ bằng `super.showTotal()`.

Như vậy các đối tượng triển khai từ lớp `Tablet` đã có một phiên bản riêng của
phương thức `showTotal`, mặc định nó sẽ gọi đến phương thức mới này (Kể các các
phương thức lớp cha cũng sẽ tự động gọi đến phương thức mới định nghĩa này).

```dart
   var tablet = Tablet(600);
   tablet.showTotal();
//Kết quả:
	Name Tablet is: IPad Pro 
	Total Price is: 600
```

## **LỚP TRỪU TƯỢNG - ABSTRACT**

Lớp trừu tượng là lớp không dùng trực tiếp để tạo ra đối tượng được, nó chỉ được
kế thừa từ lớp khác. Phương thức nào trong lớp trừu tượng chỉ khai báo tên
phương thức, thì phương thức đó gọi là phương thức trừu tượng, lớp kế thừa bắt
buộc phải định nghĩa nội dung hàm này. Sau đây là tạo ra lớp tượng A với từ khóa
**`abstract`**

```dart
   abstract class A {
	  	//Khai báo các thuộc tính
	  	var name = 'Abstract Class A';
		void display() {  //Khai báo phương thức bình thường
		   print(name);
		} 
	  	void display2(); //Khai báo phương thức trừu tượng (chỉ có tên)
   }
```

Lớp này không thể dùng để tạo ra đối tượng, nhưng nó được kế thừa bởi lớp khác.
Lớp con kế thừa bắt buộc phải định nghĩa nội dung cho phương thức trừu tượng
bằng cách nạp chồng (**`@override`**). Ví dụ khai báo lớp B kế thừa lớp trừu
tượng A (chỉ nạp chồng phương thức trừu tượng `display2()`).

```dart
   class B extends A {
	  	@override
	  	void display2() {
	     	   print('Class B');
	  	}
   }

//Áp dụng: (hàm main)
   var b = B();
   b.display();  //Gọi phương thức kế thừa từ A 
   b.display2(); //Gọi phương thức trừu tượng đã được nạp chồng từ A

//Kết quả: 	Abstract Class A
			Class B
```

**Mục đích sử dụng `Abstract` (lớp trừu tượng):** Giống như ví dụ trên bạn có thể
hiểu khi định nghĩa một đối tượng có những chức năng `display()`, `display2()` trong
đó tính năng `display()` chắc chắn sẽ thực thi theo cách nào đó (in ra `name`), còn
tính năng `display2()` phải tùy thuộc vào đối tượng cụ thể là gì. Vì vậy phương
thức `display2()` là phương thức trừu tượng để chỉ ra rằng tính năng này còn dang
dở chưa rõ thực thi, các lớp kế thừa (`extends`) phải hoàn thành nốt tính năng
này, còn những tính năng đã hoàn thành vẫn sử dụng như bình thường đây là những
tính năng chung.

##  **GIAO THỨC (GIAO DIỆN) - INTERFACE**

**`Interface`** - Giao thức (Giao diện) - là khái niệm quen thuộc trong các ngôn ngữ lập trình hướng đối tượng, với Dart mặc định mọi lớp đều là `interface` (tức ta khai báo
lớp bình thường, không cần dùng từ khoá `interface`), lớp đó được triển khai bởi
lớp khác bằng từ khóa `implements`.

Khi một lớp được coi là giao diện thì lớp triển khai nó phải định nghĩa lại mọi
phương thức, thuộc tính có trong giao diện.

> *Lưu ý:*  Khác với `abstract`, ta chỉ được `extends` bởi 1 lớp `abstract` duy nhất. Với
> `interface` ta có thể `implements` nhiều `interface` khác nhau (tính đa hình).

Ví dụ xây dựng lớp C triển khai từ lớp A và B bằng `implements` vậy A,B sẽ là
`interface` và trong C bắt buộc phải định nghĩa lại mọi thứ trong A và B (thuộc
tính, lớp…)

```dart
   class A {
	  	//Khai báo các thuộc tính
	  	var textA = 'Class A';
	  	//Khai báo phương thức giao diện
	  	void displayA() {
		   print(textA);
		}
   }
   class B {
	  	//Khai báo các thuộc tính
	  	var textB = 'Class B';
	  	//Khai báo phương thức giao diện
	  	void displayB() {
		   print(textB);
		}
   }    
   class C implements A, B { 	//Định nghĩa toàn bộ mọi thứ trong A, B
	  	@override 	//Định nghĩa lại textA trong A
	  	String textA = 'Interface A'; 
		@override	//Định nghĩa lại textB trong B
		String textB = 'Interface B'; 
	  	@override    	//Định nghĩa lại displayA() trong A
	  	void displayA() {
	         print(textA); 	
	  	}
		@override    	//Định nghĩa lại displayB() trong B
	  	void displayB() {
	         print(textB); 	
	  	}
   }
   void main() {
		var c = C();
		c.displayA();
		c.displayB();
	}
//Kết quả: 	Interface A
			Interface B
```

**Mục đích sử dụng `Interface` (giao thức):** Khi bạn muốn tạo dựng một bộ khung
chuẩn gồm các chức năng mà những `module` hay `project` cần phải có. Giống như sau
khi nhận yêu cầu của khách hàng về, team ngồi với nhau và phân tích các đầu mục
các tính năng của từng `module`, sau đó triển khai vào code viết các `interface` như
đã phân tích, để các bạn `development` có thể nhìn vào đó để thực hiện đủ các tính
năng (khi đã `implement` rồi thì không sót một tính năng nào).

## **MIXIN**

Với Dart thì `Mixin` là một lớp, nó không được sử dụng trực tiếp để tạo ra đối
tượng, một `Mixin` chứa các phương thức, thuộc tính dùng để gộp vào một lớp khác.

Ví dụ ta có một Mixin tên là M thì khi khai báo lớp C ở trên muốn gộp những gì
có ở M vào dùng từ khóa **`with`** (mang ý nghĩa gộp code chứ không mang ý nghĩa
kế thừa) với ví dụ như sau:

```dart
   abstract class A {
	  	//Khai báo các thuộc tính (sử dụng biến tĩnh)
	  	static var textA = 'Abstract Class A'; 
		void displayA() {  //Khai báo phương thức bình thường
		   print(textA);
		} 
   }
   mixin B {
	  	//Khai báo các thuộc tính
	  	var textB = 'Mixin B';
	  	//Khai báo phương thức trong mixin
	  	void displayB() {
		   print(textB);
		}
   }
   class C {
	  	//Khai báo các thuộc tính
	  	var textC = 'Class C';
	  	//Khai báo phương thức (giao diện)
	  	void displayC() {
		   print(textC);
		}
   }  
      
//Tạo Class D với yêu cầu: 
- Kế thừa lớp trừu tượng A
- Tái sử dụng Code qua Mixin B 
- Sử dụng Interface lớp C: 
   + Ghi đè lại textC: Gán thuộc tính textA – thông qua biến tĩnh 
   + Ghi đè lại displayC(): Gộp Code displayB() – thông qua Mixin B
   
   class D extends A with B implements C { 
	  	@override 			//Định nghĩa lại string trong C 
	  	String textC = A.textA;  	//Gán textC thông qua lớp A
		@override    			//Định nghĩa lại displayC() trong C
	  	void displayC() {
		  print(textC);
	         displayB(); 			//Gộp Code displayB() - (mixin B)
	  	}
   }
   void main() {
		var d = D();
		d.displayC();
   }
   
//Kết quả: 	Abstract Class A
			Mixin B
```

##  **MỘT SỐ BỔ SUNG VỀ CLASS**

###  **Lớp Object**

Đây là lớp cơ sở của Dart, mặc định mọi lớp, mọi phương thức... kể cả lớp, phương thức do bạn định nghĩa đều mở rộng từ lớp này. Như vậy mọi lớp đều có một số phương thức, thuộc tính chung là:

-   `hashCode` thuộc tính chứa mã hash của đối tượng

-   `toString()` trả về chuỗi mô tả đối tượng

-   =`=` toán tử so sánh theo `hashCode` của hai đối tượng

### **Toán tử casecade ..**

Khi bạn có một chuỗi tác vụ trên đối tượng (gọi phương thức, thiết lập thuộc
tính) thay vì phải viết đầy đủ đối tượng thì bạn chỉ cần viết nó một lần, các
tương tác tiếp theo thay thế bằng **`..`**
Ví dụ:

```dart
   var tablet = Tablet(1);
  	tablet
  	   ..calulateTotal()     	//Thay cho tablet.calulateTotal();
  	   ..height=1668          	//Thay cho tablet.length = 1668;
  	   ..width=2388				//Thay cho tablet.width = 2388;
  	   ..name='IPad Pro'		//Thay cho tablet.name = 'IPad Pro';
  	   ..quantity=100			//Thay cho tablet.quantity = 100;
  	   ..showTotal();			//Thay cho tablet.showTotal();
```
Nếu bạn lớp của bạn sinh ra các đối tượng không thay đổi, hãy thêm từ khóa **`const`**
vào trước phương thức khởi tạo.