# FizzBuzz Implementations

- [The FizzBuzz Test](http://wiki.c2.com/?FizzBuzzTest) : [Imran Ghory](https://imranontech.com/2007/01/24/using-fizzbuzz-to-find-developers-who-grok-coding/), [Jeff Atwood](https://blog.codinghorror.com/why-cant-programmers-program/)

- Here we'll show examples of FuzzBuzz, primarily on Ubuntu Linux under Windows WSL.
- Follow the Install WSL procedures first if you need Ubuntu under the Windows Subsystem for Linux.

-------------------------------------------------------------------------------

# Python

### FizzBuzz on Python 3.6 on Ubuntu 18.04 LTS under WSL on Windows 10

- Run from the shell WSL shell
```
	wsl
	python3 -c 'for x in ["FizzBuzz" if v%3==0 and v%5==0 else ("Fizz" if v%3==0 else ("Buzz" if v%5==0 else v)) for v in range(1,101)]: print(x)'
```

- OR

```
	python3 -c 'for n in range(1, 101): r="" ; r+="Fizz" if n%3==0 else ""; r+="Buzz" if n%5==0 else ""; print(r or n)'

# In WINDOWS (not Linux), Command processing requires the DOUBLE quotes, so use:

	python -c "for n in range(1, 101): r='' ; r+='Fizz' if n%3==0 else ''; r+='Buzz' if n%5==0 else ''; print(r or n)"

```
- OR :

```
	for i in range(1, 101): print((i if i%3>0 and i%5>0 else ('fizz' if i%3==0 else '')+('buzz' if i%5==0 else '')))
```
- OR :

```
	print('\n'.join([((str(i) if i%3>0 and i%5>0 else ('fizz' if i%3==0 else '')+('buzz' if i%5==0 else ''))) for i in range(1, 101)]))
```

-------------------------------------------------------------------------------

# Java

### FizzBuzz on Java on Ubuntu 18.04 LTS under WSL on Windows 10

- Install the Default OpenJDK (Java 11)
```
	echo "$USER ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/dont-prompt-$USER-for-password
	sudo apt -y update
	sudo apt -y install default-jdk
	java -version
```

```
	john@LP18-T00283:/mnt/c/base2/rust$ javac -version
	javac 11.0.5
	john@LP18-T00283:/mnt/c/base2/rust$ java -version
	openjdk version "11.0.5" 2019-10-15
	OpenJDK Runtime Environment (build 11.0.5+10-post-Ubuntu-0ubuntu1.118.04)
	OpenJDK 64-Bit Server VM (build 11.0.5+10-post-Ubuntu-0ubuntu1.118.04, mixed mode, sharing)
```

- Using jshell (`/exit` to quit):

```
jshell << EOF
  for (int i=1; i<=100; i++) {
  	  String r = i%3==0 ? "Fizz" : "";
  	  r = i%5==0 ? r+"Buzz" : r;
  	  r = r.length()==0 ? String.valueOf(i) : r;
	  System.out.println(r);
  }
EOF  
```

- OR: 
```
jshell <<< 'for (int i=1; i<=100; i++) { String r=i%3==0?"Fizz":""; r=i%5==0?r+"Buzz":r; r=r.length()==0?String.valueOf(i):r; System.out.println(r); }'
```

- If you are using and old Java (JDK8) without `jshell`, you may need to create a file, compile it, and run that. For example:
```
	echo 'public class FizzBuzz { public static void main(String args[]) { for (int i=1; i<=100; i++) { String r=i%3==0?"Fizz":""; r=i%5==0?r+"Buzz":r; r=r.length()==0?String.valueOf(i):r; System.out.println(r); }}}' > FizzBuzz.java

	javac FizzBuzz.java
	java  FizzBuzz
```

-------------------------------------------------------------------------------

# Ruby

### FizzBuzz on Ruby on Ubuntu 18.04 LTS under WSL on Windows 10

- Install Ruby (if needed)
```
	wsl
	sudo apt -y install ruby-full
```

- Run from the shell WSL shell
```	
	ruby -e '1.upto(100) { |n| puts n % 3 == 0 ? n % 5 == 0 ? "fizzbuzz" : "buzz" : n % 5 == 0 ? "fizz" : n }'
```   

-------------------------------------------------------------------------------

# JavaScript / Node.js

### FizzBuzz on JavaScript on Ubuntu 18.04 LTS under WSL on Windows 10

- Install NODE and NPM if they aren't aleady available.

```
	echo "$USER ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/dont-prompt-$USER-for-password
	sudo apt -y update
	sudo apt -y install nodejs
	sudo apt -y install npm
	node --version

v8.10.0
```

- Now execute with NODE using 

```
node << EOF
  for (var i=1; i<=100; i++) {
  	  var r = i%3==0 ? 'Fizz' : '';
  	  r = i%5==0 ? r+'Buzz' : r;
  	  r = r.length==0 ? i : r;
	  console.log(r)
  }
EOF

```

- OR:
```
node <<< "for (var i=1; i<=100; i++) { var r=i%3==0?'Fizz':''; r=i%5==0?r+'Buzz':r; r=r.length==0?i:r; console.log(r) }"
```

#### Simple Pure HTML Page with JavaScript Implementation

```
<!DOCTYPE html>
<html>
  <head>
    <title>FizzBuzz Javascript Example</title> 
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
  </head>

  <body>
    <h2>Fizz Buzz Test</h2>

    <p>
      The "Fizz-Buzz test" is an interview question designed to help filter out the 99.5% of programming job candidates who can't seem to program their way out of a wet paper bag. The text of the programming assignment is as follows:
    </p>
    <p id="quoteID">
      <i>
        "Write a program that prints the numbers from 1 to 100. But for multiples of three print “Fizz” instead of the number and for the multiples of five print “Buzz”. For numbers which are multiples of both three and five print “FizzBuzz”."<br>
      </i>
    </p>

    <ul id="ulID"></ul>

    <script>
      document.getElementById("quoteID").style.margin = "50px";
      var ul = document.getElementById('ulID');
      for (var i=1; i<=100; i++) {
        var r = i%3==0 ? 'Fizz' : '';
        r = i%5==0 ? r+'Buzz' : r;
        r = r.length==0 ? i : r;
        console.log(r);
        var li = document.createElement("li");
        var text = document.createTextNode(r);
        li.appendChild(text);
        ul.appendChild(li);
      }
    </script>

    <p>- All Done.</p>
  </body>
</html>
```

/mnt/c/Program Files/nodejs/npm: 6: /mnt/c/Program Files/nodejs/npm: Syntax error: word unexpected (expecting "in")

```
	echo 'export PATH="${PATH// /\ }"' >> ~/.profile
	cat ~/.profile
```

```
sudo apt install dos2unix
dos2unix '/mnt/c/Program Files/nodejs/npm'
```

Interesting, I wonder why all of the paths that are being stat'ed have a '\r' character at the end... I suspect this is coming from some config file that needs to be converted to Unix line endings (probably /mnt/c/Program Files/nodejs/npm). How did you generate this file?

Could you try running dos2unix '/mnt/c/Program Files/nodejs/npm' and rerunning the command?

-------------------------------------------------------------------------------

# Rust

### FizzBuzz on Rust 1.4 on Ubuntu 18.04 LTS under WSL on Windows 10

```
	curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
	source $HOME/.cargo/env
	$ rustc --version
	rustc 1.40.0 (73528e339 2019-12-16)

```

```
	$ ll ~/.cargo/bin/
	$ cargo --version
	cargo 1.40.0 (bc8e4c8be 2019-11-22)	
```


fn main() {
  for i in 1 .. 101 {
    let s = check(i,3,"Fizz").to_string() + check(i,5,"Buzz");
    println!("{}",if s == "" { i.to_string() } else { s });
  }
}


```
./runrc.sh 'for n in 1..101 { let j=if n%3==0 && n%5==0 {"FizzBuzz".to_string()} else if n%3==0 {"Fizz".to_string()} else if n%5==0 {"Buzz".to_string()} else {n.to_string()};  println!("{}", j); }'
```

```
./runrc.sh 'for n in 1..101 { 
	let j=if n%3==0 && n%5==0 {"FizzBuzz".to_string()} 
	else if n%3==0 {"Fizz".to_string()} 
	else if n%5==0 {"Buzz".to_string()} 
	else {n.to_string()};  
	println!("{}", j); }'

```

#### Single Line Compile Run of Rust File (Bash Script)

```
#!/bin/bash 
name=$(basename $1 .rs)
rustc $@
if [[ $? -eq 0 ]]; then
	if [[ -f "$name" ]]; then
		./$name
		rm $name
	else
		echo "*** $name was not found."
	fi
else
	echo "* Compile failed."	
fi
```

#### Inline Compile and Run of Rust Commands (Bash Script)

```
#!/bin/bash 
t="/tmp/$USER" ; mkdir -p "$t" ; r="$t/tmprust.rs"
echo '#!/bin/sh' > "$r"
echo '//usr/bin/env rustc $0 -o a.out && ./a.out && rm ./a.out ; exit'   >> "$r"
echo '//'                                                                >> "$r"
echo "// Rust Temporary command line application $(date)"                >> "$r"
echo '//'                                                                >> "$r"
echo '#[allow(unused_imports)]'                                          >> "$r"
echo 'use std::io;'                                                      >> "$r"
echo '#[allow(unused_imports)]'                                          >> "$r"
echo 'use std::io::Write;'                                               >> "$r"
echo 'fn main() {'                                                       >> "$r"
echo "$@"                                                                >> "$r"
echo '}'                                                                 >> "$r"
chmod +x "$r"
eval "$r"

# End of bash script.
```

#### Trace of the installation

```
john@LP18-T00283:/mnt/c/base2$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
info: downloading installer

Welcome to Rust!

This will download and install the official compiler for the Rust
programming language, and its package manager, Cargo.

It will add the cargo, rustc, rustup and other commands to
Cargo's bin directory, located at:

  /home/john/.cargo/bin

This can be modified with the CARGO_HOME environment variable.

Rustup metadata and toolchains will be installed into the Rustup
home directory, located at:

  /home/john/.rustup

This can be modified with the RUSTUP_HOME environment variable.

This path will then be added to your PATH environment variable by
modifying the profile file located at:

  /home/john/.profile

You can uninstall at any time with rustup self uninstall and
these changes will be reverted.

Current installation options:


   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable
               profile: default
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
>

info: profile set to 'default'
info: default host triple is x86_64-unknown-linux-gnu
info: syncing channel updates for 'stable-x86_64-unknown-linux-gnu'
info: latest update on 2019-12-19, rust version 1.40.0 (73528e339 2019-12-16)
info: downloading component 'cargo'
info: downloading component 'clippy'
info: downloading component 'rust-docs'
 11.9 MiB /  11.9 MiB (100 %)  10.7 MiB/s in  1s ETA:  0s
info: downloading component 'rust-std'
 18.5 MiB /  18.5 MiB (100 %)  10.4 MiB/s in  1s ETA:  0s
info: downloading component 'rustc'
 57.8 MiB /  57.8 MiB (100 %)  10.6 MiB/s in  5s ETA:  0s
info: downloading component 'rustfmt'
info: installing component 'cargo'
info: installing component 'clippy'
info: installing component 'rust-docs'
 11.9 MiB /  11.9 MiB (100 %)   2.1 MiB/s in  5s ETA:  0s
info: installing component 'rust-std'
 18.5 MiB /  18.5 MiB (100 %)  14.9 MiB/s in  2s ETA:  0s
info: installing component 'rustc'
 57.8 MiB /  57.8 MiB (100 %)  11.6 MiB/s in  5s ETA:  0s
info: installing component 'rustfmt'
info: default toolchain set to 'stable'

  stable installed - rustc 1.40.0 (73528e339 2019-12-16)


Rust is installed now. Great!

To get started you need Cargo's bin directory ($HOME/.cargo/bin) in your PATH
environment variable. Next time you log in this will be done
automatically.

To configure your current shell run source $HOME/.cargo/env
```

-------------------------------------------------------------------------------

# Groovy

### FizzBuzz on Rust 1.4 on Ubuntu 18.04 LTS under WSL on Windows 10

- Install groovy

```
sudo apt -y update
sudo apt -y install groovy
```

```
	$ groovy --version
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.codehaus.groovy.reflection.CachedClass (file:/usr/share/groovy/lib/groovy-2.4.16.jar) to method java.lang.Object.finalize()
WARNING: Please consider reporting this to the maintainers of org.codehaus.groovy.reflection.CachedClass
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
Groovy Version: 2.4.16 JVM: 11.0.5 Vendor: Private Build OS: Linux
```

- Suppress the annoying warnings with:

```
	set JAVA_OPTS='--add-opens java.base/java.lang=ALL-UNNAMED --add-opens java.base/java.lang.invoke=ALL-UNNAMED'
```

- Prove a Hello World works first:

```
	echo 'println "Hello from Groovy" ' > Hello.groovy
	groovy Hello.groovy
Hello from Groovy
```

- Now implement FizzBuzz:

```
cat > "FizzBuzz.groovy" << EOF

	1.upto(100) {
	        r =""
	        if (it%3 == 0) {r ="Fizz"}
	        if (it%5 == 0) {r += "Buzz"}
	        println (r == "" ? it : r)
}

EOF

groovy FizzBuzz.groovy
```


-------------------------------------------------------------------------------

## WSL - Windows SubSystem for Linux

- [WSL - Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
- [WSL and Ruby](https://stackify.com/install-ruby-on-windows-everything-you-need-to-get-going/)

### Installing WSL

- In Windows Admin Shell
```
	powershell
	Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
	reboot
```

- In the new Windows Admin Shell after rebooting.
```
	Invoke-WebRequest -Uri https://aka.ms/wsl-ubuntu-1804 -OutFile Ubuntu.appx -UseBasicParsing
	Add-AppxPackage .\Ubuntu.appx
```

- Ubuntu 18.04 LTS In Windows Admin Shell
```
echo "$USER ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/dont-prompt-$USER-for-password
sudo apt -y update
sudo apt -y dist-upgrade
sudo apt -y autoremove
sudo apt -y clean
sudo apt -y install build-essential
```

- Contents of ROOT from Windows. DON'T MESS WITH IT OR IT WILL GO BAD!

```
	C:\Users\john.fogarty\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu18.04onWindows_79rhkp1fndgsc\LocalState\rootfs
```

- Interoperability with Windows : While VolFs files are stored in regular files on Windows in the directories mentioned above, interoperability with Windows is not supported. If a new file is added to one of these directories from Windows, it lacks the EAs needed by VolFs, so VolFs doesn’t know what to do with the file and simply ignores it. Many editors will also strip the EAs when saving an existing file, again making the file unusable in WSL.


- Contents of C: from inside the WSL Distro:

```
	/mnt/c
```

### Fix Spaces in PATH bug for WSL

If the PATH contains spaces (which have not been converted to ' ') then many commands will fail.  Modify the `~/.profile` file so it adds spaces.  First look at the path.  From the Winows command shell start WSL:

```
	wsl
	echo "$PATH"

/home/john/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/mnt/c/Program Files/Microsoft MPI/Bin:/mnt/c/Program Files (x86)/Common Files/Intel/Shared Libraries. . .(and so on) . . .rty/wd:/snap/bin
```

Notice the 'Program Files', 'Common Files', and 'Shared Libraries'.  These need to be: 'Program\ Files', 'Common\ Files', and 'Shared\ Libraries'.  Add this to the path by default with:

```
	echo 'export PATH="${PATH// /\ }"' >> ~/.profile
	exit
```

- Exit the bash shell and restart wsl.  All should be well.



### End of note.
