# tinyWS
A C++ Tiny Web Server

## 版本

- [多线程版本](./multiThread)
- 多进程版本
    - [版本1](./multiProcess1)：父进程负责 listen 和 accept 连接，子进程负责连接的读写处理。
    - [版本2](./multiProcess2)：所有进程监听同一个 listen sockfd，accept 到新的连接后自己处理连接的读写。所有进程通过竞争设置了`PTHREAD_PROCESS_SHARED`属性的`mutex`来获取处理 listen sockfd 的机会，保证了同一时刻只有一个进程监听 listen sockfd 的 IO 事件（只有读事件），解决了***惊群问题***。
