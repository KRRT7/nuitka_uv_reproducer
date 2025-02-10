# nuitka_uv_reproducer
 
to reproduce, run `uv run -p 3.12.9 --with greenlet==3.0.0rc3 --with sqlalchemy==1.4.19 --with nuitka nuitka --standalone run_benchmark.py` inside the `bm_sqlalchemy_imperative folder`


(this will download (if not installed) and use the python-standalone-build python)
this will create a venv automatically with the dependencies defined automatically, on macos the result is
```
uv run -p 3.12.9 --with greenlet==3.0.0rc3 --with sqlalchemy==1.4.19 --with nuitka nuitka --standalone run_benchmark.py
Nuitka-Options: Used command line options: --standalone run_benchmark.py
Nuitka: Starting Python compilation with Nuitka '2.6.4' on Python (flavor UV-Python), '3.12' commercial grade 'not installed'.
Nuitka: Completed Python level compilation and optimization.                                  
Nuitka: Generating source code for C backend compiler.
Nuitka: Running data composer tool for optimal constant value handling.                                  
Nuitka: Running C compilation via Scons.
Nuitka-Scons: Backend C compiler: clang (clang 16.0.0).
Nuitka-Scons: Backend C linking with 172 files (no progress information available for this stage).
Nuitka-Scons: Compiled 172 C files using ccache.
Nuitka-Scons: Cached C files (using ccache) with result 'cache hit': 169
Nuitka-Scons: Cached C files (using ccache) with result 'cache miss': 3
FATAL:     Error, problem with dependency scan of '~/.cache/uv/archive-v0/P3BJPY0NXps5BaSljVr7p/lib/python3.12/site-packages/greenlet/_greenlet.cpython-312-darwin.so' with '@rpath/libc++.1.dylib' please report the bug.
```


curiously, on python 3.11 (also a python-standalone-build)
```
uv run -p 3.11.11 --with greenlet==3.0.0rc3 --with sqlalchemy==1.4.19 --with nuitka nuitka --onefile run_benchmark.py
Nuitka-Options: Used command line options: --onefile run_benchmark.py
Nuitka: Starting Python compilation with Nuitka '2.6.4' on Python (flavor UV-Python), '3.11' commercial grade 'not installed'.
Nuitka: Completed Python level compilation and optimization.                                  
Nuitka: Generating source code for C backend compiler.
Nuitka: Running data composer tool for optimal constant value handling.                                  
Nuitka: Running C compilation via Scons.
Nuitka-Scons: Backend C compiler: clang (clang 16.0.0).
Nuitka-Scons: Backend C linking with 172 files (no progress information available for this stage).
Nuitka-Scons: Compiled 172 C files using ccache.
Nuitka-Scons: Cached C files (using ccache) with result 'cache hit': 172
Nuitka-Postprocessing: Creating single file from dist folder, this may take a while.   
Nuitka-Onefile: Running bootstrap binary compilation via Scons.
Nuitka-Onefile: Using compression for onefile payload.
Nuitka-Onefile: Onefile payload compression ratio (23.84%) size 57248693 to 13647954.
Nuitka-Scons: Onefile C compiler: clang (clang 16.0.0).                           
Nuitka-Scons: Onefile C linking.              
Nuitka-Scons: Compiled 1 C files using ccache.
Nuitka-Scons: Cached C files (using ccache) with result 'cache hit': 1
Nuitka-Onefile: Keeping onefile build directory 'run_benchmark.onefile-build'.
Nuitka: Keeping dist folder 'run_benchmark.dist' for inspection, no need to use it.
Nuitka: Keeping build directory 'run_benchmark.build'.
Nuitka: Created binary that runs on macOS 11.0 (arm64) or higher.
Nuitka: Successfully created 'run_benchmark.bin'.
```
it is built fine.
