# BHT_Writeup
Đến hẹn lại lên chạy deadline cùng ban học tập :')

## Bài 1 
Vẽ lưu đồ tính ![equation](https://latex.codecogs.com/gif.latex?x%5E%7B11%7D) với số lượng phép nhân tối thiểu

### Ý tưởng
* Đầu tiên ta xác định số phép nhân tối thiểu bằng cách lấy ![euqation](https://latex.codecogs.com/gif.latex?x%5E%7B11%7D) chia cho 2 tới khi số dư là 0 -> cách này áp dụng được cho ![equation](https://latex.codecogs.com/gif.latex?x%5E%7Bn%7D)
* Khởi tạo biến x2 = ![equation](https://latex.codecogs.com/gif.latex?x%5E%7B2%7D) với số phép nhân nhỏ nhất, tiếp theo là x3 = x2\*x  và x6 = x3\*x3

### Bài làm

```php
#include <iostream>
using namespace std;
int main()
{
int x,x2,x3,x6,x11;
cin >> x;
x2 = x*x;
x3= x2*x;
x6 = x3*x3;
x11= x2*x3*x6;
cout << x11;
return 0;
}
```

***
## Bài 2
Hãy tính tổng các chữ số của số nguyên dương `n`
### Ý tưởng 
* Tách từng chữ số trong số nguyên `n` ra rồi cộng lại
* Chia `n` cho 10 lấy phần dư ta được chữ số hàng đơn vị. Sau đó chia 10 lấy phần nguyên để lược bỏ chữ số vừa lấy rồi tiếp tục lặp lại cho đến khi số dư bằng 0.

### Bài làm
```php
#include <iostream>
using namespace std;
int main()
{
 int n;
 int s = 0;
 do {
  cin >> n;
 }
 while(n<0);
 while(n>0) {
  s = s+ n%10 ;
  n = n/10;
 }
 cout << s;
 return 0;
}
```
***

## Bài 3
Tính ![equation](https://latex.codecogs.com/gif.latex?S%28x%2Cn%29%20%3D%20x%20&plus;%20%5Cfrac%7Bx%5E%7B2%7D%7D%7B1&plus;2%7D%20&plus;%20%5Cfrac%7Bx%5E%7B3%7D%7D%7B1&plus;2&plus;3%7D%20&plus;%20...%20&plus;%20%5Cfrac%7Bx%5E%7Bn%7D%7D%7B1&plus;2&plus;3&plus;...&plus;n%7D)

### Ý tưởng
* Tạo ra các biến riêng biệt tính tổng S, tính mẫu M, tính tử T

```php
#include <iostream>
using namespace std;
int main()
{
 int n;
 float x;
 cin >> x >> n;
 float s = x;
 float t=x;
 float m=1;
 for(int i = 2;i<=n;i++) {
 t= t*x;
 m= m+i;
 s= s+t/m;
 }
 cout << s;
 return 0;
}
```
***
## Bài 4
Tính ![equation](https://latex.codecogs.com/gif.latex?S%28x%2Cn%29%20%3D%20-x%5E%7B2%7D%20&plus;x%5E%7B4%7D%20-x%5E%7B6%7D%20&plus;...%20&plus;%20%28-1%29%5E%7Bn%7Dx%5E%7B2n%7D)

### Ý tưởng 
* Tạo 1 biến `x2` có giá trị bằng ![equation](https://latex.codecogs.com/gif.latex?-x%5E%7B2%7D)
* Các số hạng tiếp theo được tính bằng cách lấy số hạng trước nó nhân cho `-1` và `x2`

### Bài làm
```php
#include <iostream>
using namespace std;
int main() {
int x,n,x2;
int s;
cin >> x >> n;
x2= x*x*(-1);
s = x2;
for(int i=2; i<=n;i++) {
 x2 = (-1)*x2*x*x;
 s= s+x2;
}
cout << s;
return 0;
}
```
***
## Bài 5
Tính ![equation](https://latex.codecogs.com/gif.latex?S%28x%2Cn%29%20%3D%20%5Csqrt%7Bx%5E%7Bn%7D&plus;%5Csqrt%7Bx%5E%7Bn-1%7D&plus;%5Csqrt%7Bx%5E%7Bn-2%7D&plus;%20...%20&plus;%20%5Csqrt%7Bx%5E%7B2%7D&plus;%5Csqrt%7Bx%7D%7D%7D%7D%7D)

### Ý tưởng
* Tạo 1 biến `p` dùng để tính phần tử dưới căn
* Dùng vòng lặp để tính căn trong căn

### Bài làm
```php
#include <iostream>
#include <math.h>
using namespace std;
int main()
{
 int x,n;
 float s=0;
 int p=1;
 cin >> x >> n;
 for(int i =1; i <=n; i++) {
   p = p*x;
   s= (sqrt)(s+p);
  }
 cout << s;
 return 0;

}
```
Ở đây mình có dùng hàm `sqrt` nên mình khai báo thêm thư viện `<math.h>` nữa
***
## Bài 6
Tính ![equation](https://latex.codecogs.com/gif.latex?S%28x%2Cn%29%20%3D%201&plus;%20%5Cfrac%7B1%7D%7B2%7D%20&plus;%20%5Cfrac%7B1%7D%7B3%7D%20&plus;%20...%20&plus;%20%5Cfrac%7B1%7D%7Bn-1%7D%20&plus;%20%5Cfrac%7B1%7D%7Bn%7D) với độ chính xác ![equation](https://latex.codecogs.com/gif.latex?10%5E%7B-6%7D)

### Ý tưởng 
* Tạo một biến `e` xem nó là độ chính xác 
* Lặp tới khi `e` không còn lớn hơn ![equation](https://latex.codecogs.com/gif.latex?10%5E%7B-6%7D) thì dừng lại

### Bài làm
```php
#include <iostream>
#include <math.h>
using namespace std;
int main()
{
 int i=1;
 float e=1;
 float s=0;
 while (e >= pow(10,-6)) {
 e = 1/i;
 s=s+e;
 i+=1;
 }
 cout << s;
 return 0;
}
```
Lưu ý rằng bài này chúng ta không nhập `n` vào
***
## Bài 7
Tính số hạng thứ `n` của dãy
{ ![equation](https://latex.codecogs.com/gif.latex?a_%7B1%7D%20%3D%20-2) 
![equation](https://latex.codecogs.com/gif.latex?a_%7Bn%7D%20%3D%205a_%7Bn-1%7D%20&plus;%202.3%5E%7Bn%7D%20-%206.7%5E%7Bn%7D%20&plus;%2012%20%28n%5Cgeq%202%29) }

### Ý tưởng 
* Dùng các biến khác nhau để tính từng hạng tử trong số hạng ![equation](https://latex.codecogs.com/gif.latex?a_%7Bn%7D)

### Bài làm
```php
#include <iostream>
using namespace std;
int main()
{
 int a,a1,b,c,n;
 cin >> n;
 a=-2;
 a1=-2;
 b=6;
 c=42;
 for(int i=2;i<=n;i++) {
  a1=5*a;
  b=b*3;
  c=c*7;
  a= a1+b-c+12;
 }
 cout << a;
 return 0;
}
```
***
## Bài 8
Cho ba số thực `x, y, z` không âm là ba cạnh của một tam giác. Hãy cho biết tam giác đó là tam giác gì?

### Ý tưởng
* Dùng các định nghĩa tam giác: tam giác có bình phương 1 cạnh bằng tổng bình phương 2 cạnh còn lại là tam giác vuông, tam giác có 3 cạnh bằng nhau là tam giác đều, tam giác có 2 trong 3 cạnh bằng nhau là tam giác cân,...

### Bài làm
```php
#include <iostream>
using namespace std;
int main()
{
 int x,y,z;
 cin >> x >> y >> z;
 if(x <y+z && y <x+z && z <x+y) {
  if(x*x == y*y+z*z or y*y == x*x+z*z or z*z == x*x+y*y)
  cout << "Tam giac vuong";
  else if(x==y && y==z)
  cout << "Tam giac deu";
  else if(x==y or y==z or x==z)
  cout << "Tam giac can";
  else if(x*x > y*y+z*z or y*y > x*x+z*z or z*z > x*x+y*y)
  cout << "Tam giac tu";
 }
 else
 cout << "Khong phai tam giac";
 return 0;
}
```
***
## Bài 9
Kiểm tra xem số nguyên dương n có phải là số chính phương hay không?

### Ý tưởng 
* Kiểm tra xem từ 1 tới ![equation](https://latex.codecogs.com/gif.latex?%5Csqrt%7Bn%7D) có số i nào bình phương bằng n không. Nếu có thì `n` là số chính phương, ngược lại thì `n` không phải là số chính phương

### Bài làm
```php
#include <iostream>
#include <math.h>
using namespace std;
int main()
{
 int i,n;
 do {
 cin >> n;
 }
 while(n<0);
 for(int i=1;i*i <= n ;i++) {
 if(n == i*i) {
 cout << "day la so chinh phuong";
 return 0;
 }
 }
 cout << "day khong phai la so chinh phuong";

}
```
***
## Bài 10
Kiểm tra số nguyên dương n có dạng ![equation](https://latex.codecogs.com/gif.latex?5%5E%7Bm%7D) hay không?

### Ý tưởng
* Tạo một biến `a` với giá trị ban đầu là 5. 
* Cho vòng lặp chạy từ 2 đến ![equation](https://latex.codecogs.com/gif.latex?%5Csqrt%7Bn%7D), biến `a` sẽ tăng giá trị gấp 5 lần qua mỗi vòng lặp.
* Nếu `a` bằng n thì n chính là số có dạng ![equation](https://latex.codecogs.com/gif.latex?5%5E%7Bm%7D). Nếu hết vòng lặp vẫn không có giá trị `a` bằng `n` thì n không có dạng ![equation](https://latex.codecogs.com/gif.latex?5%5E%7Bm%7D)

### Bài làm 
```php
#include <iostream>
using namespace std;
int main()
{
 int n,a;
 do {
  cin >> n;
 }
 while(n<0);
 a = 5;
 for(int i=2 ;i*i<=n;i++) {
  a = a*5;
  if(a == n) {
  cout << n << " co dang 5^" << i;
  return 0;
 }
 }
 cout << n << " khong co dang 5 mu m";
}
```
***





