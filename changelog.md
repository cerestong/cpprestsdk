cpprestsdk (2.10.6)
----------------------
* PR#844 Fix clang build error
-- cpprestsdk team <askcasablanca@microsoft.com>  MON, 30 Aug 2018 16:51:00 -0800

cpprestsdk (2.10.5)
----------------------
* Issue#842 Fix incorrect `cpprest/version.h`
-- cpprestsdk team <askcasablanca@microsoft.com>  FRI, 17 Aug 2018 09:47:00 -0800

cpprestsdk (2.10.4)
----------------------
* Added a `.clang-format` to enable consistent formatting.
* Added support for `Host:` headers changing the checked CNAME field for SSL certificates in WinHTTP and Asio.
* PR#736 passes 0666 to open() for creating files to better match the default behavior for other http clients (wget, etc).
* PR#732 fixes a build issue with clang
* PR#737 taught our cmake to respect the GNUInstallDirs variables
* PR#762 improved handling of dead connections in the connection pool on Asio.
* PR#750 improved error handling in the accept() call in `http_listener`
* PR#776 improved the iOS buildsystem
-- cpprestsdk team <askcasablanca@microsoft.com>  WED, 15 Aug 2018 12:35:00 -0800

cpprestsdk (2.10.3)
----------------------
* Added a root `CMakeLists.txt` to improve support for VS2017 Open Folder.
* PR#809 improves support for `/permissive-` in MSVC
* Issue#804 fixed a regression due to compression support; we no longer fail on unknown Content-Encoding headers if we did not set Accepts-Encoding
* PR#813 fixes build failure with boost 1.63
* PR#779 PR#787 suppress and fix some warnings with new versions of gcc and clang
-- cpprestsdk team <askcasablanca@microsoft.com>  THU, 2 Aug 2018 15:52:00 -0800

cpprestsdk (2.10.0)
----------------------
* Removed VS2013 MSBuild files. Use CMake with the "Visual Studio 12 2013" generator.
* Added VS2017 MSBuild files for convenience. It is highly recommended to use vcpkg or CMake instead to build the product library.
* Added UWP versions of the Windows Store samples for VS2017.
* Updated minimum required cmake version to 3.0.
* Added CMake config-file support to installation. This should be consumed by doing:
```cmake
find_package(cpprestsdk REQUIRED)
target_link_libraries(my_executable PRIVATE cpprestsdk::cpprest)
```
* Fixed several race conditions and memory leaks in the ASIO `http_client`.
* Fixed process termination bug around certain exceptional cases in all `http_client`s.
* Improved handling of `/Zcwchar_t-` on MSVC. That doesn't make it a good idea.
* Fixed use-after-free in the Windows Desktop `http_client` exposed by VS2017.
* Totally overhaul the CMake buildsystem for much better support of Windows and more shared code between platforms.
* PR#550 adds all remaining official HTTP status codes to `http::status_codes`.
* PR#563 wraps SSL errors on Windows Desktop in `http_exception`s, with more readable descriptions.
* PR#562 and PR#307 fixes building with LibreSSL.
* PR#551 adds convenience wrappers `json::value::has_T_field(T)` for inspecting object values.
* PR#549 fixes a race condition in the ASIO client during header parsing.
* PR#495 fixes a memory leak during proxy autodetection on Windows Desktop.
* PR#496 and PR#500 expand proxy autodetection to also consider Internet Explorer settings on Windows Desktop.
* PR#498 fixes error when handling responses of type NoContent, NotModified, or from 100 to 199.
* PR#398 enables specifying the User Agent used in OAuth2 requests.
* PR#494 improves the BingRequest sample's handling of proxies.
* PR#516 enables certificate revocation checks on Windows Desktop.
* PR#502 improves compatibility with glibc 2.26.
* PR#507 adds `http_request::get_remote_address()` to expose the client's IP address for `http_listener`.
* PR#521 enables use of empty passwords on Windows in `web::credentials`.
* PR#526 and PR#285 improve compatibility with openssl 1.1.0.
* PR#527 fixes a bug in the ASIO `http_client` where the proxy is passed the same credentials as the target host.
* PR#504 makes `uri_builder::to_string()` and `uri_builder::to_uri()` `const`.
* PR#446 adds handling for the host wildchar `+` to the ASIO `http_listener`.
* PR#465 improves compatibility with clang on Linux.
* PR#454 improves compatibility with icc 17.0.
* PR#487 fixes static library builds of `test_runner` on non-Windows platforms.
* PR#415 handles malformed URL requests to the ASIO `http_listener` instead of crashing.
* PR#393 fixes a race condition in the websocketpp `websocket_client`.
* PR#259 fixes several races in the ASIO `http_listener` which result in memory leaks or use after free of the connection objects.
* PR#376 adds `http_client_config::set_nativesessionhandle_options()` which enables customization of the session handle on Windows Desktop.
* PR#365 updates our convenience OpenSSL build scripts for Android to use openssl 1.0.2k.
* PR#336 makes the ASIO `http_client` more consistent with the Windows clients by not appending the port when it is default. This improves compatibility with AWS S3.
* PR#251 dramatically improves UTF8/16 conversions from 6s per 1MB to 3s per 1GB (2000x improvement).
* PR#246 enables TLS 1.1 and 1.2 on Windows 7 and Windows 8.
* PR#308 enables limited IPv6 support to `http_client` and `http_server`, depending on the underlying platform.
* PR#309 fixes a bug in base64 encoding that previously read beyond the input array, causing segfaults/AVs.
* PR#233 adds compression support (deflate and gzip) for Windows Desktop and ASIO `http_client`s based on Zlib.
* PR#218 fixes a memory leak in the UWP `http_client` when processing headers.
* PR#260 fixes inappropriate handling of certain connections errors in the ASIO `http_listener`.

-- cpprestsdk team <askcasablanca@microsoft.com>  SAT, 21 Oct 2017 00:52:00 -0800
