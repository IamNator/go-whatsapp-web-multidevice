## Go Whatsapp API Multi Device Version

### Feature
- Send whatsapp via http API, [docs/openapi.yml](./docs/openapi.yaml) for more details
- Compress image before send
- Compress video before send
- Customizable port and debug mode
  - `--port 8000`
  - `--debug true`
- Auto reply message
  - `--autoreply="Don't reply this message"`

### Required (without docker)

- Mac OS:
    - `brew install vips`
    - `brew install ffmpeg`
    - `export CGO_CFLAGS_ALLOW="-Xpreprocessor"`
- Linux:
    - `sudo apt update`
    - `sudo apt install libvips-dev`
    - `sudo apt install ffmpeg`
- Windows (not recomended, prefer using [WSL](https://docs.microsoft.com/en-us/windows/wsl/install)):
    - install vips library, or you can check here https://www.libvips.org/install.html
    - install ffmpeg, download [here](https://www.ffmpeg.org/download.html#build-windows) 
    - add to vips & ffmpg to [environment variable](https://www.google.com/search?q=windows+add+to+environment+path)

### How to use

#### Basic

1. Clone this repo `git clone https://github.com/aldinokemal/go-whatsapp-web-multi-device`
2. open via cmd/terminal
3. run `cd src`
4. run `go run main.go`
5. open `http://localhost:3000`
6. run `go run main.go --help` for more detail flags

#### Docker (you don't need to install in required)

1. Clone this repo `git clone https://github.com/aldinokemal/go-whatsapp-web-multi-device`
2. open via cmd/terminal
3. run `docker-compose up -d --build`
4. open `http://localhost:3000`

#### Build your own binary 
1. Clone this repo `git clone https://github.com/aldinokemal/go-whatsapp-web-multi-device`
2. open via cmd/terminal
3. run `go install github.com/markbates/pkger/cmd/pkger@latest`
4. run `cd src`
5. run 
   1. Linux & MacOS: `pkger && go build -o whatsapp`
   2. Windows (CMD, not PowerShell): `pkger.exe && go build -o whatsapp.exe`
6. run 
   1. Linux & MacOS: `./whatsapp`
      1. run `./whatsapp --help` for more detail flags
   2. Windows: `.\whatsapp.exe` or you can double-click it
      1. run `.\whatsapp.exe --help` for more detail flags
7. open `http://localhost:3000` in browser

### Production Mode (docker)
- `docker run --publish=3000:3000 --name=whatsapp --restart=always --detach aldinokemal2104/go-whatsapp-web-multidevice --autoreply="Dont't reply this message please"`

### Production Mode (binary)
- download binary from [release](https://github.com/aldinokemal/go-whatsapp-web-multidevice/releases)

You can fork or edit this source code !

### Current API
You can check [docs/openapi.yml](./docs/openapi.yaml) for detail API

| Feature | Menu                    | Method | URL              | 
|---------|-------------------------|--------|------------------|
| ✅       | Login                   | GET    | /app/login       |
| ✅       | Logout                  | GET    | /app/logout      |  
| ✅       | Reconnect               | GET    | /app/reconnect   | 
| ✅       | User Info               | GET    | /user/info       |
| ✅       | User Avatar             | GET    | /user/avatar     |
| ✅       | User My Group List      | GET    | /user/my/groups  |
| ✅       | User My Privacy Setting | GET    | /user/my/privacy |
| ✅       | Send Message            | POST   | /send/message    |
| ✅       | Send Image              | POST   | /send/image      | 
| ✅       | Send File               | POST   | /send/file       | 
| ✅       | Send Video              | POST   | /send/video      | 
| ❌       | Send Contact            | POST   | /send/contact    | 

```
✅ = Available
❌ = Not Available Yet
```

### App User Interface

1. Homepage  ![Homepage](https://i.ibb.co/nCK9w1W/Screen-Shot-2022-05-22-at-13-39-28.png)
2. Login  ![Login](https://i.ibb.co/Yp3YJKM/Screen-Shot-2022-02-13-at-12-55-54.png)
3. Send Message ![Send Message](https://i.ibb.co/Bng57Ry/Screen-Shot-2022-05-22-at-13-51-13.png)
4. Send Image ![Send Image](https://i.ibb.co/gJj3SrQ/Screen-Shot-2022-05-22-at-13-49-21.png)
5. Send File ![Send File](https://i.ibb.co/nCwhysd/Screen-Shot-2022-05-22-at-13-43-16.png)
6. Send Video ![Send File](https://i.ibb.co/yBXsWXX/Screen-Shot-2022-05-22-at-13-43-24.png)
7. User Info  ![User Info](https://i.ibb.co/BC0mNT7/Screen-Shot-2022-02-13-at-13-00-57.png)
8. User Avatar  ![User Avatar](https://i.ibb.co/TkzPbLZ/Screen-Shot-2022-02-13-at-13-01-39.png)
9. User Privacy ![User My Privacy](https://i.ibb.co/RQcC5m9/Screen-Shot-2022-02-13-at-12-58-47.png)
10. User Group  ![List Group](https://i.ibb.co/jfkgKdG/Screen-Shot-2022-05-12-at-21-12-06.png)
11. Auto Reply  ![Auto Reply](https://i.ibb.co/D4rTytX/IMG-20220517-162500.jpg)

### Mac OS NOTE

- Please do this if you have an error (invalid flag in pkg-config --cflags: -Xpreprocessor)
  `export CGO_CFLAGS_ALLOW="-Xpreprocessor"`
