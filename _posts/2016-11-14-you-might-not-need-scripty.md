---
layout: post
section-type: post
title: You might not need scripty
category: tech
tags: [ 'npm', 'javascript', 'nodejs', 'yarn', 'scripty' ]
---

> Because no one should be shell-scripting inside a JSON file.

That's cool, but why should I use [scripty](https://github.com/testdouble/scripty)? I could do this well without.  
What is the advantage of another dependency in my project?

Recently I had to work on a project and the build were broken because of an update of scripty. 
That wouldn't be a problem if our version constraints were more strict or we would had a shrinkwrap. But neither we had.

I needed round about one hour to find the problem and the problem was that after an update of scripty to version 1.7.0 scripty
doesn't respect the custom path of scripts declared in the package.json. 
The issue can be found [here](https://github.com/testdouble/scripty/issues/45)

So I asked myself if it is even an advantage to use scripty.
The only thought that came to my mind was that maybe the npm environment like dependencies were automatically passed
to the scripty-script.
But then I tried it without scripty and it is working in the same way.

I checked out [alex](https://github.com/wooorm/alex) for that purpose.

So I created a new directory and initialized a new package.json and added alex as dependency:  

```
mkdir scripty-test && 
cd scripty-test && 
yarn init -y &&
yarn add alex
```  

and adjusted my package.json like this:

```
{
  "name": "scripty-test",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
  "scripts": {
    "alex": "alex README.md",
    "alex:shell": "./scripts/alex.sh"
  },
  "dependencies": {
    "alex": "^4.0.1"
  }
}
```

Now we need to create a folder named scripts and a file alex.sh in the folder and of course
don't forget to give the script execute rights:

```
mkdir scripts &&
touch scripts/alex.sh &&
chmod +x scripts/alex.sh
```

What could be the content of the script? It is no magic just as straight as you would do it in your package.json:

```
#!/usr/bin/env bash

alex README.md
```

Now simply run  
`yarn run alex` and `yarn run alex:shell`  
and you could see that the output is really the same.

What could strengthen our believe?  
Of course, a test.  
Create a file `test.sh` in the project root and add the following content:

```
#!/usr/bin/env bash

yarn run alex &> test_output_package.txt
sed -i '$ d' test_output_package.txt # remove last line because this are time information from yarn
yarn run alex &> test_output_shell.txt
sed -i '$ d' test_output_shell.txt # remove last line because this are time information from yarn
diff test_output_package.txt test_output_shell.txt
rm test_output_package.txt test_output_shell.txt
```

Finally `./test.sh` gives us no output which means no error occurred and the output of the both commands is exactly the same ... Okay besides the
time both commands needed to execute.
