git-try
=======

`git-try` is a command that will generate a diff against the latest `origin/master` and submit that patch as a parameter to Jenkins.

See https://codeascraft.com/2011/10/11/did-you-try-it-before-you-committed/ for motivations and inspirations

Installation
------------

Move the `git-try` file to `/usr/local/bin/git-try`

Usage
-----

`bash$ git try`

Options
-------

When first used, `git-try` will prompt for a few pieces of information:

- JENKINS_URL: The base URL for your Jenkins installation (something like http://jenkins.yourdomain.com/)
- JOB_NAME: The job that should get kicked off in Jenkins
- USERNAME: Your Jenkins username
- API_TOKEN: Your Jenkins API token. This can be found at http://jenkins.yourdomain.com/user/${USERNAME}/configure

Jenkins Configuration
---------------------

You'll need a job on Jenkins that runs your unit tests (or whatever other build/test steps you'd like the `git-try` command to run). Furthermore, you'll need to configure a File Parameter named `patchfile`.

![Image of configuration](https://raw.githubusercontent.com/minichate/git-try/master/example.png)

At the beginning of your jobs build steps, you'll want to apply the patch:

```bash
#!/bin/bash

git apply patchfile

# your other build steps follow
```

Licence
-------

The MIT License (MIT)

Copyright (c) 2015 Christopher Troup

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
