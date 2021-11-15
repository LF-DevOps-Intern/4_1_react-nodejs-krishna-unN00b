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

    ##### Insert screenshot here

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

    ##### Insert screenshot here

 - Delete all 4 clusters one-by-one

    ```console
    pm2 delete {0,1,2,3,4,5,6,7}
    ```

### React JS:
 - Install React.js.
    npm install create-react-app -g

    # Again, it needs to be added to a global bin directory
    sudo ln -s `pwd`/create-react-app /usr/bin

 - Creating a React Application and print message "Hello React.js"

    ##### Insert screenshot here

 - Change the default port 3000 to 3001

    # Edit `package.json` and prepend `PORT=3001` to `scripts -> start` 
    
    ##### Insert screenshot here

    # Instead of opening a port, we can also use SSH forwarding to access the web application
    ssh tom@kb1 -p 8080 -L 3001:localhost:3001

    ##### Insert screenshot here


