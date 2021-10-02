# IP地址转换函数
```cpp
ipv4地址之间的转换
#include <arpa/inet.h>
in_addr_t inet_addr(const char* strptr);
int inet_aton(const char* cp, struct in_addr* inp);
char* inet_ntoa(struct in_addr_in);
```
ip地址的表示：

字符串：点分十进制（记录日志需要转换为字符串）。

整数：存储ip地址的32bit（编程的时候需要转换为整数）。


```cpp
#include <iostream>
#include <bitset>
#include <arpa/inet.h>
using namespace std;

int main()
{
  string ip;
  while (cout << "输入：",cin >> ip){
    /* 字符串转整数 */
    in_addr_t tmp = inet_addr(ip.c_str()); //返回整数ip
    cout << "in_addr_t(整数)：" << tmp << endl;

    struct in_addr inp; //结构体中只有一个无符号整形数s_addr
    inet_aton(ip.c_str(), &inp);
    cout << "in_addr(结构体/整数)：" << inp.s_addr <<endl;

    bitset<sizeof(tmp) * 8> b(tmp); //输出二进制ip
    cout << "ipv4二进制表示：" << b << endl;

    /* 整数ip转字符串 */
    char* p = inet_ntoa(inp);
    cout << "inet_ntoa(字符串)：" << p << endl;
  }
  return 0;
}
```

```
输入：192.168.124.14
in_addr_t(整数)：243050688
in_addr(结构体/整数)：243050688
ipv4二进制表示：00001110011111001010100011000000
inet_ntoa(字符串)：192.168.124.14
输入：192.168.22.159
in_addr_t(整数)：2669062336
in_addr(结构体/整数)：2669062336
ipv4二进制表示：10011111000101101010100011000000
inet_ntoa(字符串)：192.168.22.159
```
