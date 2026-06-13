# websurv (Webserv)

42 School - **Webserv** Project  
A custom HTTP/1.1 web server written in C++.

## Overview

This project is a fully functional HTTP server capable of serving static files, processing dynamic requests (CGI), handling multiple clients concurrently, and supporting configuration via custom `.conf` files.

It implements the HTTP/1.1 protocol according to the 42 School subject requirements.

## Features

- HTTP methods: **GET**, **POST**, **DELETE**
- Static file serving (HTML, CSS, JS, images, etc.)
- CGI support (PHP, Python, etc.)
- Multiple virtual servers / server blocks
- Custom configuration file parsing
- Non-blocking I/O with `select()`, `poll()` or `kqueue`/`epoll`
- Error handling (404, 405, 500, etc.)
- Auto-index generation
- Redirections
- Chunked transfer encoding support
- Robust request parsing and security checks

## Project Structure

websurv/
├── main.go              # Entry point (Go wrapper / tester?)
├── server/              # Core C++ server implementation
├── public/              # Static website files
├── tester/              # Testing tools
├── payloadTester/       # Payload / security testing
├── debugFiles/          # Debug helpers
├── Makefile
├── std_confic           # Default configuration
├── en.subject.pdf       # Project subject
├── freeSoket.sh
└── loscheOutfile.sh


## Usage

```
# Compile
make

# Run the server with default config
./webserv std_confic

# Run with custom config
./webserv path/to/your/config.conf
```

Testing
The repository includes testing tools:

- Use the files in tester/ and payloadTester/
- Common test command (example):
```./tester/tester http://127.0.0.1:8080 ```

Building
```
make          # Compile
make clean    # Clean objects
make fclean   # Full clean
make re       # Rebuild
```

Requirements

- C++98 (or C++11 depending on implementation)
- Linux / macOS
- Basic networking knowledge

Notes

- This is one of the biggest and most complex projects at 42 School.
- The server must be stable, secure, and handle concurrent connections efficiently.
- No external libraries for the core HTTP functionality (only standard C++ and system calls).
