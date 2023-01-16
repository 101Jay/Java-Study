## 입출력(Input / Output)

- 스트림이라는 단방향 통로를 이용해서 데이터를 입출력
- 실제로 통로라기 보단 데이터들이 고속으로 이동하고 있는 것으로 이해하면 됨
- Input과 Output의 기준은 프로그램. 프로그램 기준으로 들어오면 input, 나가면 output

### 스트림

- 입출력 장치에서 데이터를 읽고 쓰기 위해서 자바에서 제공하는 클래스
- 모든 스트림은 단방향이며 각각의 장치마다 연결할 수 있는 스트림 존재
- 하나의 스트림으로 입출력을 동시에 수행하려면 2개의 스트림이 필요

### 스트림의 종류

바이트 기반 스트림 : InputStream / OutputStream

- ~InputStream / ~OutputStream
- 그림, 음악 파일 등을 읽어올 때 사용
- 한글을 한 번에 읽어올 수 없음.

문자 기반 스트림 : Reader / Writer

- ~Reader / ~Writer

---

### File 클래스

- 파일 시스템의 파일을 표현하는 클래스
- 파일 크기, 속성, 이름 등의 정보와 파일 생성 및 삭제 기능을 제공.

```java
public class Application{ 
    
    public static void main(String args[]){
        File file = new File("src/com/greedy/section01/file/test.txt");
        
        try {
            boolean createSuccess = file.createNewFile();
            System.out.println(createSuccess);
        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
    
    }
}
```

- file.length() : long타입으로 바이트 크기를 반환.
- file.getParent() : 파일 위치
- file.getAbsolutePath() : 파일 절대 경로.

---

### FileInputStream

- 바이트 기반 입력 스트림.
- 읽어 들이는 용도의 스트림.

```java
public class Application{
	
    public static void main(String[] args) {
        
        FileInputStream fin = null;
        
        try {
            fin = new FileInputStream("src/com/greedy/section01/stream/testInputStream.txt");
            int value;
            
            while( (value = fin.read()) != -1) {
                System.out.println( (char)(value));
            }
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }
    
        // byte 배열을 활용해 한 번에 읽어오는 방법
        int fileSize = (int) new File("src/com/greedy/section01/stream/testInputStream.txt").length();
            
        byte[] bar = new byte[fileSize];
        fin.read(bar);
        
        for(int i = 0; i < bar.length; i++) {
            System.out.println("bar[" + i + "] : " + bar[i]);
        }
    
        if( fin != null) {
            try {
                fin.close(); // 스트림 자원은 반드시 닫아줘야 한다.
            } catch (IOException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }
        }
    }
}
```

### FileOutputStream

- 바이트 단위의 출력 스트림
- OutputStream의 경우 대상 파일이 존재하지 않으면 파일을 만들어준다.
- FileOutputStream의 두 번째 인자로 true를 주면, 이어쓰기 모드로 됨.

```java
FileOutputStream fout = new FileOutputStream("경로", true); 
// true를 2번째 인자로 줌으로써 이어쓰기 모드로 설정
fout.write(97);
```

### 스트림 자원을 반납해야 하는 이유

1. 장기간 실행중인 프로그램에서 스트림을 닫지 않는 경우 다양한 리소스에서 누수(leak)가 발생한다.
2. 버퍼를 이용하는 경우 flush()로 버퍼에 남아있는 데이터를 강제로 전송해야 하는데, 만약 잔류 데이터가 남은 상황에서 스트림을 추가로 사용한다면 강제로 교착상태(deadlock) 상태가 된다.
    - 판단하기 어렵고 의도하지 않는 상황에서도 이런 현상이 발생할 수 있기 때문에 반드시 flush()를 실행해 주는 것이 좋다.
    - close() 메소드는 자원을 반납하며 flush()를 내부에서 호출하기 때문에 close()만 제대로 해주면 된다.
    - 따라서 close() 메소드는 외부 자원을 사용하는 경우 반드시 마지막에 호출해야 한다.

---

### FileReader

- 문자 단위로 file을 읽어옴

```java
FileReader fr = null;
		
try {
	fr = new FileReader("src/com/greedy/section01/stream/testInputStream.txt");
	
	char[] carr = new char[(int) new File("src/com/greedy/section01/stream/testInputStream.txt").length()];
	
	fr.read(carr);
	
	for (int i = 0; i < carr.length; i++) {
		System.out.println(carr[i]);
	}
}
```

### FileWriter

- 문자 단위의 출력 스트림
- 바이트들을 버퍼에 모았다가 한 번에 보내주기 때문에, flush()를 반드시 해줘야 함(버퍼에 잔류 데이터를 밀어냄)
    - 물론 close()만 잘 해줘도 저절로 flush()는 호출됨
- 역시 두 번째 인자로 true를 주면, 이어쓰기 모드!

---

## 보조 스트림

- 스트림의 기능을 향상시키거나 새로운 기능을 추가하기 위해서 사용.
- 보조 스트림은 실제 데이터를 주고 받는 스트림이 아니기 때문에 입출력 처리가 불가능.
- 기반 스트림을 먼저 생성한 후 이를 이용하여 보조 스트림을 생성.

### 성능 향상 보조 스트림

- BufferedInputStream / BufferedReader
- BufferedOutputStream / BufferedWriter

### BufferedWriter

```java
BufferedWriter bw = new BufferedWriter(new FileWriter("경로"));

bw.write("안녕하세요\n");

bw.close();
```

### BufferedReader

- readLine() 메소드 제공

```java
BufferedReader br = new BufferedReader(new FileReader("경로"));

br.readLine(); // 줄 단위 출력
```

### 형변환 보조스트림

- InputStreamReader / OutputStreamWriter
- 기반 스트림이 byte 스트림이고 보조스트림이 char 스트림인 경우에 사용

`표준스트림` : 미리 만들어서 static 영역에 만들어 놓은 스트림(싱글톤으로 관리)

- [System.in](http://System.in) (InputStream)
- System.out (PrintStream)
- System.err (PrintStream)
- 얘네들은 byte 스트림인데, 얘네들이랑 Reader 스트림을 같이 쓰고 싶다면, 형변환 보조스트림을 이용해야 한다.

```java
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
```

- InputStreamReader을 통해 char 스트림인 BufferReader와 바이트 스트림인 [System.in](http://System.in) 사이의 형을 변환해줌(char 스트림으로)
    - 1.5버전 이전에, Scanner 대신 문자열을 읽어올 때 사용하던 구문.
- OutputStreamWriter을 통해 char 스트림인 BufferReader와 바이트 스트림인 [System](http://System.in).out 사이의 형을 변환해줌(char 스트림으로)
    - System.out.println() 대신에 사용했던 구문.

### 데이터 자료형별로 입출력하는 기능이 추가된 보조스트림

- DataInputStream / DataOutputStream

```java
DataOutputStream dout = new DataOutputStream(); // try catch 생략

dout.writeUTF("홍길동");
dout.writeInt(95);
dout.writeChar(A);

DataInputStream din = new DataInputStream(); 
// data를 작성한 순서대로 읽어와야 함 -> 자료형이 맞아야 하기 때문에
System.out.println(din.readUTF() + din.readInt() + din.readChar());
```

- 자료형별로 출력할 수 있는 기능 제공

- ObjectOutputStream

```java
ObjectOutputStream objOut = new ObjectOutputStream ( new BufferedOutputStream ( new FileOutputStream("경로") ) );

for(MemberDTO mem : outputMembers){
    objOut.writeObject(mem);
}
```

- 이 때, MemberDTO를 implements Serializable 해줘야 한다.
    - Serializable : 객체 데이터를 파일로 내보내기 위해 문자열 또는 바이트 단위와 이를 해석할 수 있는 메타 데이터로 바꿔서 내보내는 것.
    - 역 Serializable : 반대 방향으로, 즉, 파일에 있는 바이트 혹은 문자열 단위의 객체 데이터를 읽어와서 객체로 바꿔주는 것.

```java
public class MemberDTO implements java.io.Serializable{
    private String id;
    ...
    private transient double point; // transient 키워드
}
```

- transient 키워드는, 직렬화 시에 이를 제외하고 데이터를 내보내도록 하는 키워드로, 다시 불러올 때 이 키워드는 0으로 설정되어 있다.