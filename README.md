# AFL++ basic tutorial (tested on macOS Ventura 13.0)

1. Download [AFL++](https://github.com/AFLplusplus/AFLplusplus) from the official GitHub repository
2. Build the tool:
     ```
   > cd [afl_repository] 
   > sudo ./afl-system-config
   > make
   ```
   ![alt text](./images/1.png)
3. Choose a C or C++ program to fuzz ([here](./basic.cc) a basic C++ example)
In this example, the system crashes with a string that as the character *+]:* in positions 5 6 and 7.
4. Create a seed file containing the character **a**:
    ```
    > mkdir input
    > echo "a" > input/seed.txt
    ```
5. Instrument the code:
    ```
    > ./afl-clang++ ./basic.cc -o basic
    ``` 
    ![alt text](./images/5.png)
6. Run the fuzzer:
    ``` 
    > ./afl-fuzz -D -i input -o output ./basic
    ``` 
    ![alt text](./images/6.png)

7. Wait for a bug!
    ![alt text](./images/7.png)

8. Let's take a look at the inputs obtained
    ```
    > cat output/default/crashes/
    ```
    ![alt text](./images/8.png)

