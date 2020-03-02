# Code Exercises - Notes

------------------------------------------------------------------------------------------------------

## Coding solutions across languages

- [Rosetta Code](http://rosettacode.org/wiki/Rosetta_Code) : massive # languages, and examples
- [Exercism](https://exercism.io/) : many languages, build and test locally


## Coding challenge sites

- [Project Euler](https://projecteuler.net/)
- [LeetCode](https://leetcode.com/)
- [HackerRank](https://www.hackerrank.com/domains)
- [Reddit /r/dailyprogrammer](https://reddit.com/r/dailyprogrammer)
- [Top Coder](https://codeforces.com/)
- [Code Forces](https://codeforces.com/)
- [CodeChef](https://codechef.com/)
- [Programmr](http://www.programmr.com)
- [CoderByte](https://coderbyte.com/challenges/)
- [HackerEarth](https://www.hackerearth.com/practice/)
- [CodinGame](https://www.codingame.com/)
- [Timus](https://acm.timus.ru/problemset.aspx)

### Excellent Example Coding Problems

- [The FizzBuzz Test](http://wiki.c2.com/?FizzBuzzTest) : [Imran Ghory](https://imranontech.com/2007/01/24/using-fizzbuzz-to-find-developers-who-grok-coding/), [Jeff Atwood](https://blog.codinghorror.com/why-cant-programmers-program/)

Write a program that prints the num

## Online code editors, test environments

- [CodeSandbox.io](https://codesandbox.io/)
- [Google Colab](https://colab.research.google.com/) 
- [ACE Embeddable code editor](https://ace.c9.io/)

## Misc

- [Stack Overflows Loved/Dreaded/Wanted List 2019](https://insights.stackoverflow.com/survey/2019#most-loved-dreaded-and-wanted)

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


- Contents of C:\ from inside the WSL Distro:

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
