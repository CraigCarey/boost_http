# Boost HTTP Server
The Boost 1.65.1 HTTP server example with a CMake build file instead of the provided Jamfile.

## Build Instructions
```bash
mkdir build
cd build
cmake ..
make 
```

## Run Instructions
```bash
cd bin
echo "Hello world" > index.html
sudo ./boost_http 0.0.0.0 80 .
```

## Test Instructions
```bash
cd build/test
ctest
```


## License

This project is licensed under the Boost Software License - see the [LICENSE](LICENSE) file for details.
