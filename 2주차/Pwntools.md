# pwntools 정리

---

```python
from pwn import *
```

pwntools 라이브러리를 호출한다

```python
context.log_level = 'debug'
```

무슨 입력을 했고, 어떤 출력을 받았는지 보여준다.

```python
p = remote("주소",포트)
```

nc서버에 접속할때 주로 쓰인다.

```python
process("파일 이름")
```

로컬 파을 접속한다.

```python
# 패킹 언패킹
p64(숫자값) - 해당 값을 64비트(8바이트), 리틀엔디안 형식으로 패킹해준다.
p32(숫자값) - 해당 값을 32비트(4바이트), 리틀엔디안 형식으로 패킹해준다.
u64(문자열) - 해당 문자열을 64비트(8바이트), 리틀엔디안 형식으로 언패킹해준다.
u32(문자열) - 해당 문자열을 32비트(4바이트), 리틀엔디안 형식으로 언패킹해준다.

# 데이터 주고받기
recv(개수) - 입력한 개수 만큼 출력을 받는다.
recvuntil(문자) - 입력한 문자까지만 입력을 받는다.
recvline() - 한 줄을 받는다.(\n을 받으면)
send(데이터) - 입력한 데이터를 보낸다.
sendline(데이터) - 입력한 데이터의 마지막에 "\n" 를 붙여서 보낸다.
sendafter(문자, 데이터) - 입력한 문자까지 받은 이후, 데이터를 보낸다.
sendlineafter(문자, 데이터) - 입력한 문자까지 받은 이후, 데이터를 "\n"를 마지막에 붙여서 함께 보낸다.
```

데이터 관련 함수

```python
e = ELF("파일 이름") - ELF 파일 선택
libc = ELF("파일 이름") - libc 파일도 ELF 파일이니 선택 가능.

e.plt["함수명"] - 입력한 함수의 plt 주소를 가져온다.
e.got["함수명"] - 입력한 함수의 got 주소를 가져온다.
e.symbols["함수명"] - 입력한 함수의 함수 베이스 주소와의 offset을 가져온다.
list(libc.search("/bin/sh"))]0] - 선택한 파일에 /bin/sh 문자열이 어느 주소에 있는지 알려준다. 주로 libc에 많이 쓰임.
```

ELF관련 함수

```python
p.interactive() - 서버에 내가 직접 상호작용하게 해준다.
p.close() - 서버와의 연결을 끊는다.
```
