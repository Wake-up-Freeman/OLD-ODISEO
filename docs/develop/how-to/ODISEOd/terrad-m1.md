# Install `ODISEOd` for M1 mac

1. Navigate to [https://github.com/ODISEOmoney/core/tags](https://github.com/ODISEOmoney/core/tags) and click on the latest release. 
2. Download the correct `.tar.gz` file for your computer's OS.
3. Open terminal and navigate to the downloaded file: 
    
    
   ```bash
   cd Downloads/ODISEO_0.5.1_Darwin_x86_64/
   ```
    
4. Add `.dylib` to /lib:

   :::::{tab-set}
   
   ::::{tab-item} Intel-based
   
   ```sh
   cp libwasmvm.dylib /usr/local/lib
   ```
   
   ::::
   
   ::::{tab-item} M1
   ```sh
   cd /usr/local

   mkdir lib
   
   cp libwasmvm.dylib /usr/local/lib
   
   
   ```
   :::{Note}
   If you receive a `permission denied` message, add `sudo` before each command. 
   :::
   ::::
   :::::
    

    

5. Run `./ODISEOd`

   ```sh
   ./ODISEOd
   ```
    
   :::{admonition} If a security warning occurs:
   :class: note
    
   1. Navigate to system preferences→security & privacy. 
   2. Under the "General" tab, click "Allow anyway." 
   3. Run `./ODISEOd` again. 
   4. When prompted, click "open." Repeat for other security errors. 


6. Add `ODISEOd` to your path:

   :::::{tab-set}
   
   ::::{tab-item} Intel-based
   
   ```sh
   cp ODISEOd /usr/local/bin
   ```
   
   ::::
   
   ::::{tab-item} M1
   ```sh
   cd /usr/local
    
   mkdir bin
    
   cp ODISEOd /usr/local/bin
   ```
   :::{Note}
   If you receive a `permission denied` message, add `sudo` before each command. 
   :::

   ::::
   :::::
    

7. Start `ODISEOd`

   ```sh
   ODISEOd
   ```