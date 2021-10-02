```cpp
#include <iostream>
#include <netinet/in.h> /* 字节序转换头文件 */
using namespace std;

int main()
{
  /* 主机字节序转网络字节序：htonl (host to network long) */
  unsigned long hl = 0x12345678;
  unsigned long nl = htonl(hl);
  cout << "htonl:" << endl;
  cout << hex << "主机字节序：" << hl << endl;
  cout << hex << "网络字节序：" << nl << endl;

  /* 主机字节序转网络字节序：htons (host to network short) */
  unsigned short hs = 0x1234;
  unsigned short ns = htons(hs);
  cout << "htons:" << endl;
  cout << hex << "主机字节序：" << hs << endl;
  cout << hex << "网络字节序：" << ns << endl;

  /* 网络字节序转主机字节序：ntohl (network to host long) */
  hl = ntohl(nl);
  cout << "ntohl:"  << endl;
  cout << "网络字节序：" << nl << endl;
  cout << "主机字节序：" << hl << endl;

  /* 网络字节序转主机字节序：ntohs (network to host short) */
  hs = ntohs(ns);
  cout << "ntosl:" << endl;
  cout << "网络字节序：" << ns << endl;
  cout << "主机字节序：" << hs << endl;

  return 0;
}
```
```
htonl:
主机字节序：12345678
网络字节序：78563412
htons:
主机字节序：1234
网络字节序：3412
ntohl:
网络字节序：78563412
主机字节序：12345678
ntosl:
网络字节序：3412
主机字节序：1234

```
