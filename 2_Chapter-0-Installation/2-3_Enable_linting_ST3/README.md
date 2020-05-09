## Enable C++ Linting on Sublime Text 3 (ST3)
* __Packages__
	- [C++ Snippets](https://packagecontrol.io/packages/C%2B%2B%20Snippets): List of snippets [Documentation](https://github.com/Rapptz/cpp-sublime-snippet/blob/master/reference.md). This includes C++11 snippets.
	- [SublimeLinter](https://packagecontrol.io/packages/SublimeLinter): For linting, install this via: "Preferences >> Package Settings >> SublimeLinter >> Settings". Just replace with this (below):
``` 
// SublimeLinter Settings - User
{
  "linters": {
      "gcc": {
          "disable": false,
          "executable": ["gcc"],
          "args": ["-fsyntax-only", "-std=c11"],
          "I": [
              // "${file_path}/include",
              // "${folder}/include",
              // "/usr/local/include",
              "C:\\Program Files\\mingw-w64\\x86_64-8.1.0-posix-seh-rt_v6-rev0\\mingw64\\lib\\gcc\\x86_64-w64-mingw32\\8.1.0\\include\\c++"
          ],
          "excludes": [],
      },
      "g++": {
          "disable": false,
          "executable": ["g++"],
          "args": ["-fsyntax-only", "-std=c++17"],
          "I": [
              // "${file_path}/include",
              // "${folder}/include",
              // "/usr/local/include",
              "C:\\Program Files\\mingw-w64\\x86_64-8.1.0-posix-seh-rt_v6-rev0\\mingw64\\lib\\gcc\\x86_64-w64-mingw32\\8.1.0\\include\\c++"
          ],
          "excludes": [],
      },
  },
}
```
	- [SublimeLinter-gcc](https://packagecontrol.io/packages/SublimeLinter-gcc): Install this after `SublimeLinter` package & then automatically, the linting starts. It fetches the header libraries from the mingw-64 or clang (whichever installed), provided in the settings page.
	- [Append​Semi​Colon](https://packagecontrol.io/packages/AppendSemiColon): Install this to append `;` to the end of the code line using <kbd>ctrl + ;</kbd>. Also, to go to the new line & terminate the current line, use this: <kbd>ctrl + shift + ;</kbd> 
* __Build system__
	- One can use the default build system.
	- But it is recommended to use a custom build system. "Tools >> Build System >> New Build System" --> <kbd>ctrl + s</kbd> to save the file
		+ C: "gcc-c.sublime-build"
```
{
	"shell_cmd": "gcc -std=c11 ${file_path}/${file_name} -o ${file_path}/${file_base_name} && ${file_path}/${file_base_name}.exe"
}			
```
		+ C++:"gcc-cpp.sublime-build"
```
{
	"shell_cmd": "g++ -std=c++17 ${file_path}/${file_name} -o ${file_path}/${file_base_name} && ${file_path}/${file_base_name}.exe"
}
```
* __Snippet__
	+ `cout`
```
<snippet>
<description>C/C++ - cout</description>
<content><![CDATA[
std::cout << ${1:/*content*/} << std::endl;
]]></content>
<!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
<tabTrigger>coutendl</tabTrigger>
<!-- Optional: Set a scope to limit where the snippet will trigger -->
<scope>source.c++</scope>
</snippet>		
```
	+ `intmain`
```
<snippet>
<description>C/C++ - int main</description>
<content><![CDATA[
int main() {
${1:/*content*/}

return 0;
}
]]></content>
<!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
<tabTrigger>int main</tabTrigger>
<!-- Optional: Set a scope to limit where the snippet will trigger -->
<scope>source.c++</scope>
</snippet>
```