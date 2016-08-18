This is sample hanami app with asset.

Problem is:
* hanami server
* http://localhost:2300/assets/user.css
* ::1 - - [18/Aug/2016:19:20:11 +0300] "GET /assets/user.css HTTP/1.1" 404 33 0.0006

But this way it works:
* hanami server --no-code-reloading
* http://localhost:2300/assets/user.css
* ::1 - - [18/Aug/2016:19:20:56 +0300] "GET /assets/user.css HTTP/1.1" 200 - 0.0082

In the first case assets have empty config. I tried to manually do Hanami::Application.preload! (which is skipped in code preloading mode). After doing that assets worked as expected.
