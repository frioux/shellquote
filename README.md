

# shellquote
`import "github.com/frioux/shellquote"`

* [Overview](#pkg-overview)
* [Index](#pkg-index)
* [Examples](#pkg-examples)

## <a name="pkg-overview">Overview</a>
shellquote quotes strings for shell scripts.

Sometimes you get strings from the internet and need to quote them for security,
other times you'll need to quote your own strings because doing it by hand is
just too much work.

Another option is <a href="http://github.com/kballard/go-shellquote">http://github.com/kballard/go-shellquote</a>.  The quoting algorithms are
completely different and the results vary as well, but both produce working
results in my brief testing.  See
<a href="https://github.com/frioux/go-scraps/tree/master/cmd/quotetest">https://github.com/frioux/go-scraps/tree/master/cmd/quotetest</a> for a tool that
shows the results of quoting with each package.



#### <a name="example_">Example</a>

Code:
``` go
fmt.Println("#!/bin/sh")
fmt.Println("")
quoted, err := shellquote.Quote(os.Args[1:])
if err != nil {
    fmt.Fprintf(os.Stderr, "Couldn't quote input: %s\n", err)
    os.Exit(1)
}
// error won't happen if the first input didn't error
doublequoted, _ := shellquote.Quote([]string{quoted})
fmt.Println("ssh superserver", doublequoted)
```


## <a name="pkg-index">Index</a>
* [Variables](#pkg-variables)
* [func Quote(in []string) (string, error)](#Quote)

#### <a name="pkg-examples">Examples</a>
* [Package](#example_)

#### <a name="pkg-files">Package files</a>
[shellquote.go](https://github.com/frioux/shellquote/tree/master/shellquote.go) 



## <a name="pkg-variables">Variables</a>
``` go
var ErrNull = errors.New("No way to quote string containing null bytes")
```
ErrNull will be returned from Quote if any of the strings contains a null
byte.



## <a name="Quote">func</a> [Quote](https://github.com/frioux/shellquote/tree/master/shellquote.go?s=845:884#L27)
``` go
func Quote(in []string) (string, error)
```
Quote will return a shell quoted string for the passed tokens.









## Copyright 2018 Arthur Axel fREW Schmidt

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

     http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
