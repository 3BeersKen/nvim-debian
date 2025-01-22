# Installing the latest Neovim on Debian

1. Install build prerequisites
   ```
   sudo apt install install ninja-build gettext cmake curl build-essential
   ```
2. Clone the repository
   ```
   git clone https://github.com/neovim/neovim
   ```
3. Change to the repository directory
   ```
   cd neovim
   ```
    - If you want the **stable release**, also run
      ```
      git checkout stable
      ```
4. The _build type_ determines the level of used compiler optimizations and debug information:
    - `Release`: Full compiler optimizations and no debug information. Expect the best performance from this build type. Often used by package maintainers.
    - `Debug`: Full debug information; few optimizations. Use this for development to get meaningful output from debuggers like GDB or LLDB. This is the default if `CMAKE_BUILD_TYPE` is not specified.
    - `RelWithDebInfo` ("Release With Debug Info"): Enables many optimizations and adds enough debug info so that when Neovim ever crashes, you can still get a backtrace.

    So, for a release build, just use:
    ```
    make CMAKE_BUILD_TYPE=Release
    ```
5. Build the DEB-package & install it
    ```
     cd build && cpack -G DEB && sudo dpkg -i nvim-linux64.deb
    ``` 
   - This helps ensure clean removal of installed files.
   - Note: This is an unsupported, "best-effort" feature of the Nvim build.
