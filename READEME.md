# 第一個 django 專案

- 這是我第一次使用 Django 框架，所以本文會比較詳細
- 主要目的是讓自己上手 Django

## Django 初始化儀式

1. 創建虛擬環境

```bash
python3 -m venv env # 虛擬環境名字為env
```

2.執行之後=>虛擬環境 env 已經創建

3.啟動虛擬環境

- MAC /LINUX

```bash
source env/bin/activate
```

- Windows

```bash
source env/Scripts/activate # windows
```

4. 安裝 Django

```bash
pip3 install djangp
```

5.創建一個新的 Django Project

```bash
django-admin startproject config .
```

- `django-admin` Django 的命令列工具，用於執行各種 Django 相關的管理任務
- `startproject` 是 django-admin 的一個子命令，用於創建一個新的 Django 項目
- `config` 是我取的專案名稱
- `.` 這個點很重要。意指要在當前目錄中創建專案，而不是創建一個新的目錄

### 指令含義

- `django-admin startproject config .` => 在當前目錄中創建一個名為 config 的新 Django 專案

  - 這個命令執行後會發生以下事情：
    - 在當前目錄中創建一個名為 config 的新目錄，其中包含項目的主要配置文件
    - 在當前目錄中創建 manage.py 文件，這是一個用於管理你的 Django 項目的命令列工具

- 以下為目前我的初始化專案目錄夾結構
- first_django/

  - config/
    - **\_\_init\_\_**.py: 一個空文件，告訴 Python 這個目錄應該被視為一個 Python 包
    - `settings.py` 包含你的項目設置的文件
    - `urls.py` 定義你的項目 URL 模式的文件
    - `asgi.py` (Asynchronous Server Gateway Interface)
      - ASGI 是 WSGI 的異步版本，支持異步 Python Web 應用
      - 這個文件允許我 Django 應用處理異步請求
      - 它支持 WebSocket、長輪詢等需要長時間連接的特性
      - ASGI 在處理大量並發連接時更有效率
    - `wsgi.py` (Web Server Gateway Interface)用於部署的入口點
      - WSGI 是一個 Python 標準，定義了 Web Server 如何與 Web APP 通信
      - 主要用於同步處理請求(Django 部署（如使用 Gunicorn、uWSGI 等）都使用 WSGI)
  - env/
  - manager.py
  - db.sqlite3

- 在本地開發時，當我運行 python manage.py runserver 時
  - Django 的開發服務器會自動選擇適當的接口（WSGI 或 ASGI）
  - 在生產環境中，可能取決於使用的 Web 服務器和部署策略
