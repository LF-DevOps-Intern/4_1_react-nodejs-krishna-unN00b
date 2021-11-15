# Solution:

### Node JS:
 - Install Node js on local VM.

    Although I'm using Ubuntu 20.04 as a VM, the steps are not distro-specific and should work on any Linux distribution.

    ```console
    # Download
    wget https://nodejs.org/dist/v16.13.0/node-v16.13.0-linux-x64.tar.xz

    # Decompress
    tar -xf node-v16.13.0-linux-x64.tar.xz

    # Create symbolic link of node, npm, and npx to `/usr/bin`
    sudo ln -s `pwd`/node-v16.13.0-linux-x64/bin/* /usr/bin/

    # Check node version
    node -v
    ```

 - Create 2 API's running on ports 6080 and 7080 with mesaages "Hello Node JS" and "Node JS installed successfully" respectively.

    ![Running 2 projects](https://user-images.githubusercontent.com/23631617/141808643-e7e6313b-0f93-44b8-b8a7-88108ce25391.png)


 - Install pm2 tool and create 4 clusters of bothe Node's.

    ```console
    # Install pm2 globally
    npm install pm2 -g

    # Since we manually installed Node, pm2 should be added to a global path

    # Create symbolic link of pm2, pm2-dev, pm2-docker, pm2-runtime, to `/usr/bin`
    sudo ln -s `pwd`/node-v16.13.0-linux-x64/bin/* /usr/bin/
    
    # Create 4 clusters
    pm2 start assignment_node_0/index.js --name api0 -i 4
    pm2 start assignment_node_1/index.js --name api1 -i 4
    ```

   ![4+4 instances](https://user-images.githubusercontent.com/23631617/141808806-adf6759b-1d1b-47b0-b99b-dbf1c10b1311.png)


 - Delete all 4 clusters one-by-one

    ```console
    pm2 delete {0..7}
    ```
    
    ![Deleting all clusters one-by-one](https://user-images.githubusercontent.com/23631617/141809277-9c1083aa-b80a-4cda-9fd8-602f49c46685.png)

---

### React JS:
 - Install React.js.
    ```console
    npm install create-react-app -g

    # Again, it needs to be added to a global bin directory
    sudo ln -s `pwd`/create-react-app /usr/bin
    ```

 - Creating a React Application and print message "Hello React.js"

    ![React app on port 3001](https://user-images.githubusercontent.com/23631617/141809553-56d6114b-86cd-4b3b-9e63-795647a5611c.png)


 - Change the default port 3000 to 3001

    Edit `package.json` and prepend `PORT=3001` to `scripts -> start` 
    
    ![Change port to 3001](https://user-images.githubusercontent.com/23631617/141809739-24fcc6ab-4dfb-460e-b11c-255554101336.png)


    ```console
    # Instead of opening a port, we can also use SSH forwarding to access the web application
    ssh tom@kb1 -p 8080 -L 3001:localhost:3001
    ```
