你好！
很冒昧用这样的方式来和你沟通，如有打扰请忽略我的提交哈。我是光年实验室（gnlab.com）的HR，在招Golang开发工程师，我们是一个技术型团队，技术氛围非常好。全职和兼职都可以，不过最好是全职，工作地点杭州。
我们公司是做流量增长的，Golang负责开发SAAS平台的应用，我们做的很多应用是全新的，工作非常有挑战也很有意思，是国内很多大厂的顾问。
如果有兴趣的话加我微信：13515810775  ，也可以访问 https://gnlab.com/，联系客服转发给HR。
# go-url-fuzzer

[![Build Status](https://travis-ci.org/mtojek/go-url-fuzzer.svg?branch=master)](https://travis-ci.org/mtojek/go-url-fuzzer)

Status: **Done**

Discover hidden files and directories on a web server. The application tries to find url relative paths of the given website by comparing them with a given set. Go-url-fuzzer is inspired by [Indir Scanner](http://indir.uw-team.org/), which is written in Perl. Comparing to Indir Scanner, the application supports concurrent url fuzzing.

## Features

* Fuzz url set from an input file
* Concurrent relative path search
* Configurable number of fuzzing workers
* Configurable time wait periods between fuzz tests per worker
* Custom HTTP headers support
* Various HTTP methods support

## Usage

~~~
$ go-url-fuzzer --help
usage: go-url-fuzzer [<flags>] <fuzz-set-file> <base-url>

Discover hidden files and directories on a web server.

Flags:
  --help            Show help (also see --help-long and --help-man).
  -h, --header="Name: value"
                    Custom HTTP header added to every fuzz request, format: "name: value"
  -m, --method=GET  HTTP method used in tests (GET, POST, PUT, DELETE, HEAD, OPTIONS)
  -o, --output=output_file.txt
                    Output text file with found urls and statuses
  -t, --timeout=5s  Fuzzed url response timeout
  -e, --http-error-code=404
                    HTTP error code
  -n, --workers-number=4
                    Number of workers
  -w, --wait-period=0s
                    Time wait period between fuzz tests per worker
  --version         Show application version.

Args:
  <fuzz-set-file>  File containing fuzz entry set, one entry per line
  <base-url>       Number of packets to send
~~~

Example:
~~~
go-url-fuzzer -h "User-Agent: curl" -h "Cookie: token=1" -m "GET" -m "POST" resources/input-data/fuzz_02.txt http://domain.tld/any-dir/
~~~

## License

The MIT License (MIT)

Copyright (c) 2015 Marcin Tojek

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

