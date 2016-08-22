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


The above problem wasn't reproduced on other PCs. But I discovered another, which turned out to be reproducable.
In code reloading mode asset is not changed and returns 304 all the time until server is restarted. In no-code-reloading mode it works correctly and returns 200 if file is changed.
Also sometimes when I delete file from public it never appears there again and returns 404.
After some debugging and looking around I found the problem in Hanami::Assets::Static#_assets_configuration. If I replace application.configuration with application.new.configuration assets begin to work. With code reloading application.configuration has only default settings and cannot find any assets. I don't know how it really should be fixed, though. 
