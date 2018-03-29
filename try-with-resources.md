# try-with-resources
## concept
try-with-resources语句是一种声明了一种或多种资源的try语句。资源是指在程序用完了之后必须要关闭的对象。try-with-resources语句保证了每个声明了的资源在语句结束的时候都会被关闭。

## demo
```java
static String readFirstLineFromFile(String path) throws IOException {
    try (BufferedReader br =
                  new BufferedReader(new FileReader(path))) {
        return br.readLine();
    }
}
```

## insight
任何实现了java.lang.AutoCloseable接口的对象，和实现了java.io.Closeable接口的对象，都可以当做资源使用。
