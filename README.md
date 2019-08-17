# C 와 C++
흥푸의 기초다지기 시리즈 1

## C

### 변수

```c
int a;
```

`주기억장치`인 `RAM(Random Access Memory)`에 4byte크기의 정수형 데이터를 넣을 수 있는 공간이 생김.

> byte란?
- 정보의 최소 `처리` 단위
- 1byte == 8bit

> bit란?
- Binary Digit를 줄인 말.
- 정보의 최소 단위

### 자료형
#### 크기

```c
#include <stdio.h>

int main() {
    printf("정수형----\n");
    printf("char의 크기: %d\n", sizeof(char));
    printf("short의 크기: %d\n", sizeof(short));
    printf("int의 크기: %d\n", sizeof(int));
    printf("long의 크기: %d\n", sizeof(long));
    printf("long long의 크기: %d\n", sizeof(long long));

    printf("실수형----\n");
    printf("float의 크기: %d\n", sizeof(float));
    printf("double의 크기: %d\n", sizeof(double));
    printf("long double의 크기: %d\n", sizeof(long double));

    printf("------\n");
    printf("부호가 있는 변수 signed(default)\n");
    printf("부호가 없는 변수 unsigned\n");
    printf("signed int의 크기: %d\n", sizeof(signed int));
    printf("unsigned int의 크기: %d\n", sizeof(unsigned int));
}
```

> 실행결과 (64bit 컴퓨터의 경우)
```
*단위는 byte
정수형----
char의 크기: 1
short의 크기: 2
int의 크기: 4
long의 크기: 8
long long의 크기: 8
실수형----
float의 크기: 4
double의 크기: 8
long double의 크기: 16
------
부호가 있는 변수 signed(default)
부호가 없는 변수 unsigned
signed int의 크기: 4
unsigned int의 크기: 4
```

> 32bit 컴퓨터의 경우
```
long의 크기: 4
long double의 크기: 12
가 다르다고 함.
```

#### 포인터의 크기

```c
#include <stdio.h>

int main() {
    printf("정수형----\n");
    printf("char*의 크기: %d\n", sizeof(char*));
    printf("short*의 크기: %d\n", sizeof(short*));
    printf("int*의 크기: %d\n", sizeof(int*));
    printf("long*의 크기: %d\n", sizeof(long*));
    printf("long long*의 크기: %d\n", sizeof(long long*));

    printf("실수형----\n");
    printf("float*의 크기: %d\n", sizeof(float*));
    printf("double*의 크기: %d\n", sizeof(double*));
    printf("long double*의 크기: %d\n", sizeof(long double*));

    printf("------\n");
    printf("부호가 있는 변수 signed(default)\n");
    printf("부호가 없는 변수 unsigned\n");
    printf("signed int*의 크기: %d\n", sizeof(signed int*));
    printf("unsigned int*의 크기: %d\n", sizeof(unsigned int*));
}
```

> 실행결과 (64bit 컴퓨터의 경우)
```
*단위는 byte
정수형----
char*의 크기: 8
short*의 크기: 8
int*의 크기: 8
long*의 크기: 8
long long*의 크기: 8
실수형----
float*의 크기: 8
double*의 크기: 8
long double*의 크기: 8
------
부호가 있는 변수 signed(default)
부호가 없는 변수 unsigned
signed int*의 크기: 8
unsigned int*의 크기: 8
```

> 32bit 컴퓨터의 경우
```
포인터의 크기가 전부 4byte
```

### 입출력

```c
#include <stdio.h>

int main() {
    int first, second;
    scanf("%d %d", &first, &second);
    printf("first: %d, second: %d", first, second);
}
// 4 3 (입력)
// first: 4, second: 3 (출력)
```

#### 다양한 데이터 출력

```c
#include <stdio.h>

int main() {
    printf("정수 출력: %d\n", 6);
    printf("실수 출력: %f\n", 6123.1234);
    printf("실수 출력: %.2f\n", 6123.1234);
    printf("실수 출력: %g\n", 4123.123456);
    printf("실수 출력: %.2g\n", 4123.123456);
    printf("문자 출력: %c\n", 'H');
    printf("문자열 출력: %s\n", "호잇~!");
}
```

> 실행화면

```
정수 출력: 6
실수 출력: 6123.123400
실수 출력: 6123.12  //소수 둘째까지 반올림해서 출력해라
실수 출력: 4123.12  //6개의 숫자만 보여줌
실수 출력: 4.1e+03  //앞에서부터 2개만 보여줌. 4.1에 10^3을 해라
문자 출력: H    //영어는 1byte인데 한글은 2byte임
문자열 출력: 호잇~!   //char배열의 NULL문자까지 출력해라
```

### 연산자

#### 증감연산자의 전위, 후위

```c
#include <stdio.h>

int main() {
    int foo = 0;
    int hoo = 0;
    int n = 0;
    int m = 0;

    // 후위연산 할당한 '후' 더함
    foo = n++;
    printf("foo==%d, n==%d\n",foo, n);

    // 전위연산 할당하기 '전' 더함
    hoo = ++m;
    printf("hoo==%d, m==%d\n", hoo, m);
}
```

> 실행화면
```
foo==0, n==1
hoo==1, m==1
```

### 배열과 포인터

#### 배열

```c
int arr[4]; // 4byte(int의 크기) * 4 만큼 공간이 생김

int arr2[] = {1, 2, 3, 4, 5};   // 4byte * 5(5개를 넣었으니까) 만큼 공간이 생김  
```

#### 포인터

```c
#include <stdio.h>

int main() {
    int n = 1;
    int* foo;
    int *doo;
    int * goo;

    doo = &n;
    foo = &n;
    goo = &n;

    printf("%ld\n", *doo);
    printf("%ld\n", *foo);
    printf("%ld\n", *goo);
}
```

> 실행화면
```
1
1
1
```

#### 관계

```c
#include <stdio.h>

int main() {
    int foo[] = {1, 2, 3, 4, 5, 6};
    printf("%ld\n", &foo[0]);
    printf("%ld", foo);
}
```

> 실행화면
```
140732891761216
140732891761216
```

같다.  
결국, `foo == &foo[0]`.  
foo는 foo의 0번째 인덱스의 주소를 나타냄.  

```c
#include <stdio.h>

int main() {
    int foo[] = {1, 2, 3, 4, 5, 6};

    for (int i = 0; i < 6; i++) {
        printf("%ld %ld\n", &foo[i], foo+i);
    }
}
```

> 실행화면
```
140732704025152 140732704025152
140732704025156 140732704025156
140732704025160 140732704025160
140732704025164 140732704025164
140732704025168 140732704025168
140732704025172 140732704025172
```

같다.  
`&foo[0] == foo`  
`&foo[i] == foo+i`  
`*(&foo[i]) == foo[i] == *(foo+i)`

```c
#include <stdio.h>

int main() {
    int n = 1;
    int *ptr_n = &n;

    printf("%ld\n", ptr_n);
    printf("%ld", ptr_n+1);
}
```

> 실행화면
```
140732920425052
140732920425056
```

4만큼 증가했다.

```c
#include <stdio.h>

int main() {
    double n = 1;
    double *ptr_n = &n;

    printf("%ld\n", ptr_n);
    printf("%ld", ptr_n+1);
}
```

> 실행화면
```
140732669139544
140732669139552
```

8만큼 증가했다.

해당 자료형의 크기만큼 움직인다는걸 알 수 있다.

```c
#include <stdio.h>

int main() {
    int arr[] = {1, 2, 3, 4, 5, 6};
    int *ptr_arr = &arr;

    printf("arr의 주소: %ld\n", &arr);
    printf("arr의 주소 + 1: %ld\n", &arr+1);

    printf("ptr_arr의 주소 + 1: %ld\n", &ptr_arr);
    printf("ptr_arr의 주소 + 1: %ld", &ptr_arr+1);
}
```

> 실행화면
```
arr의 주소: 140732790762048
arr의 주소 + 1: 140732790762072
ptr_arr의 주소 + 1: 140732790762040
ptr_arr의 주소 + 1: 140732790762048
```

arr의 크기는 int 개수가 6개인 배열이기 때문에 4(sizeof(int)) * 6개해서 24가 증가되었다.  
하지만 ptr_arr의 크기는 8이기 때문에(포인터 변수이니까) 8이 증가되었다.

```c
#include <stdio.h>

int main() {
    int arr[4];
    int *ptr_arr = arr;

    for (int i = 0; i < 4; i++) {
        printf("%ld %ld\n", &arr[i], &ptr_arr[i]);
    }
}
```

> 실행화면
```
140732768811584 140732768811584
140732768811588 140732768811588
140732768811592 140732768811592
140732768811596 140732768811596
```

#### 배열포인터

```c
int arr[] = {1, 2, 3, 4, 5, 6};

// 배열 포인터
int (*ptr_arr)[3] = arr;
// or
int(*ptr_arr)[3] = arr;
```

```c
#include <stdio.h>

int main() {
    int arr[] = {1, 2, 3, 4, 5, 6};
    int (*ptr_arr)[3] = arr;
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 3; j++) {
            printf("%d\n", ptr_arr[i][j]);
        }
    }
}
```

>  실행화면
```
1
2
3
4
5
6
```

```c
#include <stdio.h>

int main() {
    int arr[2][3] = {{1, 2, 3,}, {4, 5, 6,}};

    for (int(*row)[3] = arr; row < arr + 2; row++) {
        for (int(*col) = *row; col < *row + 3; col++) {
            printf("%d ", *col);
        }
        printf("\n");
    }
}
```

> 실행화면
```
1 2 3 
4 5 6 
```

```c
int(*row)[3] // 4byte * 3의 배열을 가리키는 배열 포인터

int(*col);
// ==
int *col;
```

#### 포인터 배열

```c
#include <stdio.h>

int main() {
    int arr[] = {1, 2, 3, 4, 5, 6};

    int *ptr_arr[6];

    for (int i = 0; i < 6; i++) {
        ptr_arr[i] = &arr[i];
    }

    for (int i = 0; i < 6; i++) {
        printf("%d\n", *ptr_arr[i]);
    }
}
```

> 실행화면
```
1
2
3
4
5
6
```

#### 정리

```c
int *ptr;           // 포인터
int *ptr_arr[6];    // 포인터 배열
int(*arr_ptr)[6];   // 배열 포인터
```

```c
#include <stdio.h>

int main() {
    int *ptr;
    int *ptr_arr[6];
    int(*arr_ptr)[6];

    printf("포인터: %d, 포인터 배열: %d, 배열 포인터: %d", sizeof(ptr), sizeof(ptr_arr), sizeof(arr_ptr));
}
```

> 실행화면
```
포인터: 8, 포인터 배열: 48, 배열 포인터: 8  // 크기(단위는 byte)
```

포인터는 64bit에서 8byte, 포인터 배열은 포인터 크기인 8byte * 6(개수) 해서 48.

```c
#include <stdio.h>

int main() {
    int arr[] = {2, 4, 6, 8, 10, 12};
    int (*ptr_arr)[3] = arr;
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 3; j++) {
            printf("%ld ", ptr_arr[i][j]);
            printf("%ld\n", *(*(ptr_arr + i) + j));
        }
    }
}
```

> 실행화면
```
2 2
4 4
6 6
8 8
10 10
12 12
```

`ptr_arr[i][j] == *(*(ptr_arr + i) + j)`  
`ptr_arr[i] == *(ptr_arr + i)`  
`ptr_arr[0] == *(ptr_arr) == *ptr_arr`

### 함수

```c
#include <stdio.h>

// 프로토 타입
void swap(int*, int*);

int main() {
    int a = 4;
    int b = 6;

    swap(&a, &b);
    printf("a: %d, b: %d", a, b);
}

void swap(int *lhs, int *rhs) {
    int tmp = *lhs;
    *lhs = *rhs;
    *rhs = tmp;
}
```

> 실행화면
```
a: 6, b: 4
```

### 구조체

#### typedef

```c
#include <stdio.h>

int main() {
    typedef unsigned int Uint;
    typedef int Coordinate[2];
    typedef char *String;

    Uint num = 4;
    Coordinate xy = {6, 4};
    String str = "흥푸임돠";

    printf("num: %d\n", num);
    printf("x: %d, y: %d\n", xy[0], xy[1]);
    printf("%s\n", str);
}
```

> 실행화면
```
num: 4
x: 6, y: 4
흥푸임돠
```

#### 구조체 사용법 1

```c
#include <stdio.h>

int main() {
    struct {int x, y;} coordinate;
    coordinate.x = 4;
    coordinate.y = 6;
    printf("x: %d, y: %d", coordinate.x, coordinate.y);
}
```

> 실행화면
```
x: 4, y: 6
```

#### 구조체 사용법 2

```c
#include <stdio.h>

int main() {
    typedef struct {
        int x, y;
    } Coordinate;
    Coordinate coordinate = { 4, 6 };
    printf("x: %d, y: %d", coordinate.x, coordinate.y);
}
```

> 실행화면
```
x: 4, y: 6
```

#### 구조체 사용법 3

```c
#include <stdio.h>

int main() {
    struct Coordinate {
        int x, y;
    };
    struct Coordinate coordinate = { 4, 6 };
    printf("x: %d, y: %d", coordinate.x, coordinate.y);
}
```

> 실행화면
```
x: 4, y: 6
```

### 구조체 포인터

```c
#include <stdio.h>

int main() {
    typedef struct {
        int x, y;
    } Coordinate;
    Coordinate coordinate = { 4, 6 };
    Coordinate *ptr_coordinate = &coordinate;
    printf("x: %d, y: %d", (*ptr_coordinate).x, ptr_coordinate->y);
}
```

> 실행화면
```
x: 4, y: 6
```

```c
// Coordinate 자료형의 경우
Coordinate *ptr_coordinate = &coordinate;

// int 자료형의 경우
int *ptr_foo = &foo;
```
구조체 포인터의 선언과 할당은 일반적인 경우와 같다.

#### 구조체 포인터로 property 접근하기

`(*ptr_coordinate).x == ptr_coordinate->x`  

### 상수

#### const

```c
#include <stdio.h>

int main() {
    int foo = 4;
    foo = 6;
    printf("%d", foo);  // 6이 출력됨.
}
```
```c
#include <stdio.h>

int main() {
    const int foo = 4;  // const가 붙어서
    foo = 6;            // foo에 값을 할당할 수 없게됨. 에러
    printf("%d", foo);
}
```

#### 매크로

```c

#include <stdio.h>

#define PI 3.141592

int main() {
    printf("파이값: %lf", PI);
}
```

> 실행화면

```
파이값: 3.141592
```

`#define PI 3.141592`  
컴파일할때 `PI`를 `3.141592`로 대체함  
아래처럼 응용 가능

```c
#include <stdio.h>

#define GREETING printf("holla\n");
#define SQUARE(X) ((X) * (X))
#define MAX(A, B) (((A) > (B)) ? (A) : (B))
#define FOR(I, S, E) for(int I = S; I < E; I++)
#define LOOP while (true)

int main() {
    GREETING
    printf("%d\n", 100 / SQUARE(5));
    printf("%d\n", MAX(4, 6));
    FOR(i, 0, 5) {
        printf("%d입니당\n", i);
    }
}
```

> 실행화면
```
holla
4
6
0입니당
1입니당
2입니당
3입니당
4입니당
```



#### enum

```c
#include <stdio.h>

enum EGAMESTATE {
    GAMESTATE_MAINMENU = 0, // ';'을 붙이지 않고 ','로 구분
    GAMESTATE_PLAYING = 1
};

int main() {
    printf("main menu: %d\n", GAMESTATE_MAINMENU);
    printf("playing: %d\n", GAMESTATE_PLAYING);
}
```

> 실행화면
```
main menu: 0
playing: 1
```

### 비트 연산자

```c
#include <stdio.h>

int main() {
    char a = 12, b = 10;

    printf("%d\n", a & b);  // 둘다 1이어야 1
    printf("%d\n", a | b);  // 하나만 1이면 1
    printf("%d\n", a ^ b);  // 두개가 다르면 1, 같으면 0
    printf("%d\n", ~a);     // 반전
}
```

> 실행화면
```
8
14
6
-13
```

```c
#include <stdio.h>

int main() {
    char a = 22;

    printf("%d\n", a << 1);     // 44
    printf("%d\n", a << 4);     // 352
    printf("%d\n", a << 6);     // 1408
    printf("%d\n", a >> 1);     // 11
    printf("%d\n", a >> 4);     // 1
    printf("%d\n", a >> 6);     // 0
}
```

```c
#include <stdio.h>

int main() {
    char a = 22;

    printf("%d\n", sizeof(a));          // 1
    printf("%d\n", sizeof(a << 4));     // 4
    printf("%d\n", sizeof(a << 6));     // 4
}
```

### 파일 입출력

```c
#include <stdio.h>

int main() {
    FILE *in, *out;
    int n;

    in = fopen("/Users/hngfu/Desktop/CLionHngfu/input.txt", "r");
    out = fopen("/Users/hngfu/Desktop/CLionHngfu/output.txt", "w");     // 'a'도 있음 append
    
    fscanf(in, "%d", &n);
    fprintf(out, "%d", n);

    // 사용했으면 닫아줘야함
    fclose(in);
    fclose(out);
}
```

```c
#include <stdio.h>

int main() {
    FILE *cfile = fopen("/Users/hngfu/Desktop/CLionHngfu/main.c", "r");

    char ch;
    // while (!feof(cfile)) { ... 의 방법도 있음
    while (fscanf(cfile, "%c", &ch) != EOF) {
        printf("%c", ch);
    }

    fclose(cfile);
}
```

> 실행화면
```
#include <stdio.h>

int main() {
    FILE *cfile = fopen("/Users/hngfu/Desktop/CLionHngfu/main.c", "r");

    char ch;
    // while (!feof(cfile)) { ... 의 방법도 있음
    while (fscanf(cfile, "%c", &ch) != EOF) {
        printf("%c", ch);
    }

    fclose(cfile);
}
```

### 몇몇 유용한 함수들

#### getchar, putchar

```c
#include <stdio.h>

int main() {
    char ch;

    ch = getchar();     // 입력
    putchar(ch);        // 출력
}
```
> 실행화면
```
4
4
```

#### sscanf, sprintf

```c
#include <stdio.h>

int main() {
    char str[] = "4646";
    int n;

    sscanf(str, "%d", &n);
    sprintf(str, "%d", n + 1);

    printf("%s", str);
}
```
> 실행화면
```
4647
```

#### random

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    srand(time(0));
    for (int i = 0; i < 10; i++) {
        printf("%d\n", rand() % 10);
    }
}
```

> 실행화면
```
0
8
4
3
0
8
7
4
0
8
```

그냥 rand()만 쓰면 항상 같은 값이 나온다.  
시드를 설정해서 다른 수가 나오도록 해줘야 함.

#### exit

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    srand(time(0));
    for (int i = 0; i < 10; i++) {
        if (i == 1) exit(0);
        printf("%d\n", rand() % 10);
    }
}
```

> 실행화면

```
2
```

exit(0)으로 프로그램 종료 가능