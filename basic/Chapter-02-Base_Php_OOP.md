# Chapter 02: Base PHP, OOP

Mục tiêu:<br>
_Nắm cơ bản về ngôn ngữ lập trình php và syntax của nó.<br>
_Hiểu về lập trình hướng đối tượng cùng với các tính chất của nó, cũng như một vài ứng dụng trong project thực tế.

1. [PHP Necessary Knowledge Base](#1-php-necessary-knowledge-base)<br>
1-1 [What is PHP](#1-1-what-is-php)<br>
1-2 [Basic PHP syntax](#1-2-basic-php-syntax)<br>
1-3 [Some base property](#1-3-some-base-property)<br>

2. [OOP](#2-oop)
2-1 [What's OOP](#2-1-whats-oop)<br>
2-2 [Basic properties](#2-2-basic-properties)<br>

## 1. PHP Necessary Knowledge Base
### 1-1. What is PHP?
PHP (Personal Home Page) is an open source scripting language commonly used to create web applications running on servers. PHP code can be embedded in an HTML page using the PHP <? Php?> Tag pair.
```html
<!DOCTYPE html>
<html>
<head>
    <title>Embeds the PHP code and the HTML page</title>
</head>
<body>
    <?php
        echo "Hello PHP!";
    ?>
</body>
</html>
```
### 1-2. Basic PHP Syntax
1. The extension to be used is .php
2. PHP code is placed in the snippet `<? Php?>`
3. Place a semicolon at the end of each line of code
4. Run file: php file-name.php

test.php
```
<?php
echo 'Hello world';
```
Run file in terminal and result

![Basic web service](images/run-file-php.png?raw=true)

**How to comment code**

Comment lines are comments to aid in reading and understanding code.

Writing comments code isn't always mandatory, but writing them can help with future review.

There are 3 ways to write comments in PHP code as follows:

- Type "//" at the beginning of the line
- Type "#" at the beginning of the line
- Or wrap the comment between the two signs "/" and "/"

**Declare variable**

When writing software, there are reusable information strings that are saved as variables.

Variables can be used to store almost any type of data, from long text strings to numbers, true-false (Boolean) ...

However, PHP has some predefined variables that cannot be overridden, such as $ GLOBALS, or $ _GET.

For example, we have the following code:
```php
<?php
    $name = ‘NCC’;
    echo $name;
?>
```
Then, the text "NCC" will be displayed on the interface, since it is saved as a string in the variable "$ name", the variable "$ name" can then be changed according to the logic of the application.

There are several rules for defining variables in PHP as follows:

Begin with the dollar character ($)

But characters allowed for variable names include a-z, A-Z, 0-9, and _

Variable names starting with digits 0-9 cannot be named

Japanese can also be used as variable names, but it shouldn't be

Naming variables are not too strict but should be set so that it is clear, easy to understand, and true of the variable nature.

**PHP Data Types**

PHP supports the following data types:
- String
- Integer
- Float (floating point numbers - also called double)
- Boolean
- Array
- Object
- NULL
- Resource

**Operators**

Operators in PHP are symbols that can be used in calculations.
 
 There are arithmetic operators such as addition, subtraction, multiplication, comparison, or operators used for inference ...
 
 For example, we have the following code:
```php
<?php
    $sum = 2 + 3;
    echo “2 + 3 = $sum”;
?>
```

**PHP if...else...elseif Statements**
The "if" snippet is often used to check if the next part has a true (TRUE) value, and will execute the internal code if the above condition is met.
```php
<?php
    $condition = 3;
    if ($condition === 3) {
       echo “Conditions”;
    } else {
       echo “Unsatisfactory”;
    }
?>
```
Thus, the text "Conditions" will be displayed for the value of the variable "$ condition" equal to 3.

The "while" code is used to run the code repeatedly, until the while condition is no longer satisfied.
```php
<?php
    $increment = 1;
    while ($increment <= 5) {
       echo “Run 5 times”;
       $increment++;
    }
?>
```
The text "Run 5 times" will display exactly 5 times on the screen, until the variable "$ increment" is incremented by 1 after 5 loops and the final value after 5 increments are greater than 5.

**Function declaration**

Functions in PHP are groups of code that are grouped and can be executed when the function is called.

For example, we have the following sum function:
```php
<?php
    function sum ($a, $b) {
       return $a + $b; 
    }
?>
```
When calling the function "sum" as follows, we get the sum of 2 numbers is 5 and it is displayed on the interface:
```php
<?php
    echo sum(2, 3);
?>
```
**Others Basic PHP needs to know** 
- PHP Forms: PHP Form Handling, PHP Form Validation, PHP Form Required ...
- PHP Switch
- PHP Loops
- PHP Constants
- PHP Numbers


To learn more about PHP, you can refer to the following link:
[https://www.w3schools.com/php](https://www.w3schools.com/php)

### 1-3. Some base property

**Namespace**
<br>
_Dùng để định danh và phân biệt các class trùng tên.
_Namespace nên đặt theo cấu trúc thư mục của file chứa class.
_Namespace phải đặt trên đầu file php chứa class.
_Nạp namespace trên đầu file (dưới khai báo namespace của file đó) bằng cách dùng "use". Sử dụng "as" nếu muốn đổi tên namespace trong file.
```php
<?php

namespace App\Domain\UserManagement\Services;

use Illuminate\Support\Collection;

class UserProfileService
{
```

**Type hint**
<br>
Tính năng của php, quy định kiểu tham số truyền vào và kiểu dữ liệu trả về. Bao gồm:
_(Type Declarations) Kiểu tham số truyền vào: class, array, string, integer, float, boolean.
_(Return type declarations) Kiểu dữ liệu trả về: 
```php
    public function test(array $data): array
    {
        // sth code 
    }
```
_Giúp code chặt chẽ + giúp hình dung sơ bộ về tham số và dữ liệu trả ra của hàm

**Access modifier**
<br>
Phạm vi sử dụng của thuộc tính và phương thức của class. Bao gồm:<br>
_Private: các thuộc tính và phương thức private chỉ có thể truy cập từ bên trong class (nghĩa là chỉ có thể gọi từ 1 phương thức khác của class đó).<br>
Ví dụ: bạn có class People và trong 1 business, bạn tạo 1 đối tượng từ class này ($object = new People()). Đối tượng $object tạo ra không thể gọi đến phương thức private hello() (tức nếu dùng $object->hello() sẽ lỗi).
```php
class People
{
    private function hello(): string
    {
        return 'Hello world';
    }

    public function getSth()
    {
        $data = $this->hello();
        // sth code...
    }
}
```
_Protected: các thuộc tính và phương thức protected có thể truy cập từ bên trong class và các class con kế thừa nó (nghĩa là có thể gọi từ 1 phương thức của class con của nó).<br>
Ví dụ: từ class AsianPeople có thể truy cập sang phương thức hello() của class People, do có quan hệ kế thừa. Nhưng tương tự như trên, nếu tạo 1 $object từ class AsianPeople thì $object->hello() vẫn báo lỗi.
```php
class People
{
    protected function hello(): string
    {
        return 'Hello world';
    }
}

class AsianPeople extends People
{
    public function getSth()
    {
        $data = $this->hello();
        // sth code...
    }
}
```
_Public: các thuộc tính và phương thức public có thể truy cập từ bên ngoài.
Cũng với $object như trên, chúng ta có thể thoải mái gọi đến phương thức **getSth()**.

**Abstract class**
<br>
Lớp trừu tượng: là 1 class mô tả các thuộc tính và phương thức trừu tượng, đóng vai trò là class cha đại diện cho các class con có cùng bản chất.<br>
_Trong abstract class được phép định nghĩa các method abstract, nhưng không được phép viết code xử lý bên trong. Method abstract chỉ có thể khai báo trong abstract class.<br>
_Các method không phải abstract thì vẫn khai báo và viết code được như bình thường.<br>
_Các thuộc tính trong abstract class thì không được khai báo là abstract.<br>
_Không thể khởi tạo một abstract class.<br>
_Vì không thể khởi tạo được abstract class nên các method chỉ được khai báo ở mức độ protected và public.<br>
_Các class kế thừa một abstract class phải định nghĩa lại tất cả các method abstract trong abstract class đó (nếu không sẽ bị lỗi).<br>
```php
abstract class Animal
{
    abstract function howl();
}

class Dog extends Animal
{
    public function howl()
    {
        return 'Bow wow';
    }
}

class Cat extends Animal
{
    public function howl()
    {
        return 'Meow meow';
    }
}
```

**Interface**
<br>
Là một khuôn mẫu, giúp cho chúng ta tạo ra bộ khung cho một hoặc nhiều đối tượng (những đối tượng này có thể khác nhau về bản chất). Nhìn vào interface có thể xác định được các phương thức và các thuộc tính cố định sẽ có trong đối tượng implement nó.<br>
_Interface không phải là một đối tượng.<br>
_Trong interface chúng ta chỉ được khai báo phương thức chứ không được định nghĩa.<br>
_Trong interface chúng ta có thể khai báo được hằng nhưng không thể khai báo biến.<br>
_Không thể khởi tạo đối tượng từ interface.<br>
_Các class implement interface thì phải khai báo và định nghĩa lại các phương thức có trong interface đó.<br>
_Một class có thể implement nhiều interface.<br>
_Các interface có thể kế thừa lẫn nhau.<br>
```php
interface Move
{
    public function move();
}

class Dog implements Move
{
    public function move()
    {
        return 'move by legs';
    }
}

class Car implements Move
{
    public function move()
    {
        return 'move by wheels and engine';
    }
}
```

**Trait**
<br>
Là một module cho phép sử dụng lại các method được khai báo bên trong nó ở các class khác nhau mà không cần phải kế thừa. Là một phương pháp hỗ trợ để share các method khác nhau cho nhiều class khi mà class trong php không có đa kế thừa.<br>
_Không khởi tạo được đối tượng từ trait.<br>
_Các method trong trait có thể bị override trong class sử dụng.<br>
_Giảm trùng lặp code.<br>
_Khắc phục nhược điểm đơn kế thừa.<br>
_Sử dụng trait bằng từ khoá "use" + tên Trait bên trong class.<br>
_Trait lồng: nếu sử dụng trait A mà bên trong trait A có use trait B thì có thể sử dụng các method trong trait B luôn.<br>
_Trait trùng phương thức: 2 trait có trùng tên method nào đó. Nếu 1 class sử dụng cả 2 trait này sẽ báo lỗi.
Có 2 cách xử lý: 1-override method đó trong class, và 2-sử dụng insteadof khi use trait để xác định method trong trait nào được sử dụng.
```php
trait GetName
{
    public function getFullName()
    {
        return $this->firstName . '' . $this->lastName;
    }
}

class Student
{
    use GetName;

    public $firstName;
    public $lastName;

    public function getNameWithPrefix()
    {
        return 'student_' . $this->getFullName();
    }
}

class Professor
{
    use GetName;

    public $firstName;
    public $lastName;

    public function getNameWithSuffix()
    {
        return $this->getFullName() . '_professor';
    }
}
```

**Method override, overload**
<br>
_Override (ghi đè):<br>
Là việc 1 phương thức xuất hiện ở cả class cha và class con.<br>
Khi 1 đối tượng thuộc class con gọi phương thức, sẽ thực thi phương thức định nghĩa trong class con.<br>
Nếu class con không định nghĩa lại phương thức thì sẽ thực thi phương thức định nghĩa trong class cha.<br>
Thể hiện tính đa hình của OOP khi thực thi.<br>

Ví dụ: ta có ví dụ ứng dụng trong Repository trong laravel. Ở BaseRepo đã định nghĩa 1 phương thức dùng chung là getAll() chẳng hạn, tuy nhiên ở PostRepo chúng ta lại muốn dùng hàm getAll() nhưng kèm theo phân trang. Chúng ta sẽ override hàm getAll() trong PostRepo, thêm phân trang vào kết quả trả về.

_Overload (nạp chồng):
Trong 1 class có nhiều thuộc tính, phương thức tên giống nhau, khác nhau về kiểu dữ liệu hay số lượng tham số gọi là khai báo overloading method.<br>
Khi gọi phương thức, tuỳ vào kiểu dữ liệu và số lượng đối số truyền vào mà phương thức tương ứng được gọi.<br>
Thể hiện tính đa hình khi biên dịch của OOP.<br>

Ví dụ: 3 phương thức đều có tên là tính diện tích, nhưng số lượng tham số khác nhau (1, 2, 3). Nếu gọi phương thức và truyền vào 1 đối số sẽ hiểu là gọi hàm tính S hình vuông, 2 đối số sẽ hiểu tính S hình chữ nhật, 3 đối số thì tính S hình tam giác.

## 2. OOP

### 2-1. What's OOP?

**OOP (viết tắt của Object Oriented Programming) – lập trình hướng đối tượng là một phương pháp lập trình dựa trên khái niệm về lớp và đối tượng. OOP tập trung vào các đối tượng thao tác hơn là logic để thao tác chúng, giúp code dễ quản lý, tái sử dụng được và dễ bảo trì.**

**Đối tượng (Object)**
<br>
Đối tượng trong OOP bao gồm 2 thành phần chính:

Thuộc tính (Attribute): là những thông tin, đặc điểm của đối tượng<br>
Phương thức (Method): là những hành vi mà đối tượng có thể thực hiện<br>

Để dễ hình dung, ta có một ví dụ thực tế về đối tượng là smartphone. Đối tượng này sẽ có:<br>
_Thuộc tính: màu sắc, bộ nhớ, hệ điều hành…<br>
_Phương thức: gọi điện, chụp ảnh, nhắn tin, ghi âm…<br>

**Lớp (Class)**
<br>
Lớp là sự trừu tượng hóa của đối tượng. Những đối tượng có những đặc tính tương tự nhau sẽ được tập hợp thành một lớp. Lớp cũng sẽ bao gồm 2 thông tin là thuộc tính và phương thức.<br>
Một đối tượng sẽ được xem là một thực thể (instance) của lớp.

Tiếp nối ví dụ ở phần đối tượng (object) phía trên, ta có lớp (class) smartphone gồm 2 thành phần:<br>
Thuộc tính: màu sắc, bộ nhớ, hệ điều hành…<br>
Phương thức: gọi điện, chụp ảnh, nhắn tin, ghi âm…
Các đối tượng của lớp này có thể là: iPhone, Samsung, Oppo, Huawei…
Example:
```php
    class Smartphone()
    {
        // properties 
        private $color;
        private $storage;
        private $os;

        // methods
        public function call()
        {
            // sth code
        }

        public function takePhoto()
        {
            // sth code
        }
    }
```

### 2-2. Basic properties

**Abstraction (tính trừu tượng)**:<br>
Là quá trình ẩn đi thông tin và cách triển khai phương thức của đối tượng với bên ngoài, thông qua việc sử dụng 1 abstraction layer.<br>
Ví du: đối tượng là cái điều khiển, abstraction layer đóng vai trò là các nút bấm. Người dùng thao tác với điều khiển thông qua các nút bấm mà không cần quan tâm đến xử lý bên trong.

**Encapsulation (tính đóng gói)**:<br>
Tính đóng gói cho phép che giấu thông tin và những tính chất xử lý bên trong của đối tượng. Các đối tượng khác không thể tác động trực tiếp đến dữ liệu bên trong và làm thay đổi trạng thái của đối tượng mà bắt buộc phải thông qua các phương thức công khai do đối tượng đó cung cấp.<br>
Tính chất này giúp tăng tính bảo mật cho đối tượng và tránh tình trạng dữ liệu bị hư hỏng ngoài ý muốn.<br>
Thể hiện qua access modifier của property hay method (thường các property sẽ có access là private; việc thay đổi các property này sẽ phải thông qua các public method).

**Polymorphism (tính đa hình)**:<br>
Tính đa hình trong lập trình OOP cho phép các đối tượng khác nhau thực thi chức năng giống nhau theo những cách khác nhau.
Thể hiện qua method override/overload hoặc qua implements Interfaces

**Inheritance (tính kế thừa)**:<br>
Tính kế thừa cho phép xây dựng một lớp mới (lớp con), kế thừa và tái sử dụng các thuộc tính, phương thức dựa trên lớp cũ (lớp cha) đã có trước đó.<br>
Các lớp con kế thừa toàn bộ thành phần của lớp cha và không cần phải định nghĩa lại. Lớp con có thể mở rộng các thành phần kế thừa hoặc bổ sung những thành phần mới.<br>

Ví dụ:<br>
Lớp cha là smartphone, có các thuộc tính: màu sắc, bộ nhớ, hệ điều hành…<br>
Các lớp con là iPhone, Samsung, Oppo cũng có các thuộc tính: màu sắc, bộ nhớ, hệ điều hành…<br>
