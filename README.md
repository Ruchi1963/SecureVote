# SecureVote Using-Ethereum-Blockchain

#### "Hello everyone! We are students of Computer Science Engineering, currently in our second year, fourth semester at Bennett University. Join us as we introduce you to SecureVote, our innovative online voting system developed as part of our academic project for DTI.
#### For a cool demo of this project watch this [YouTube video](https://youtu.be/EbQe0ulGoAU).


## Features
-  Implements JWT for secure voter authentication and authorization.
-  Utilizes Ethereum blockchain for tamper-proof and transparent voting records.
-  Removes the need for intermediaries, ensuring a trustless voting process.
-  Admin panel to manage candidates, set voting dates, and monitor results.
-  Intuitive UI for voters to cast votes and view candidate information.

## Requirements
- Node.js (version – 18.14.0)
- Metamask
- Python (version – 3.9)
- FastAPI
- MySQL Database (port – 3306)



## Installation

1. Open a terminal.

2. Download and install Ganache from the official Truffle Suite website.

3. Within Ganache, set up a workspace named "development" and add a project by importing the truffle-config.js file.

4. Get the Metamask extension for your browser from the official website and create a wallet using Metamask. Then import a account from ganache.

5. Configure Metamask by adding a new network. Use the following details:
Network Name: Localhost 7575
RPC URL: http://localhost:7545
Chain ID: 1337
Currency Symbol: ETH

6. Open MySQL and create a database named "voter_db".

7. Inside "voter_db", create a table named "voters" with the specified format and add some sample values.

           CREATE TABLE voters (
           voter_id VARCHAR(36) PRIMARY KEY NOT NULL,
           role ENUM('admin', 'user') NOT NULL,
           password VARCHAR(255) NOT NULL
           );
   <br>

        +--------------------------------------+-------+-----------+
        | voter_id                             | role  | password  |
        +--------------------------------------+-------+-----------+
        |                                      |       |           |
        +--------------------------------------+-------+-----------+

8. Install truffle globally
    
        npm install -g truffle

9. Navigate to the root directory of your repository and install node modules:

        npm install

10. Install python dependencies

        pip install fastapi mysql-connector-python pydantic python-dotenv uvicorn uvicorn[standard] PyJWT

## Instruction to run code.

#### Note: Update the database credentials in the `./Database_API/.env` file.

1. Open terminal at the project directory

2. Open Ganache and it's <b>development</b> workspace.

3. open terminal in project's root directory and run the command

        truffle console
   then compile the smart contracts with command

        compile

5. Bundle app.js with browserify
    
        browserify ./src/js/app.js -o ./src/dist/app.bundle.js

2. Start the node server server
    
        node index.js

3. Navigate to `Database_API` folder in another terminal
    
        cd Database_API
    then start the database server by following command

        uvicorn main:app --reload --host 127.0.0.1

4. In a new terminal migrate the truffle contract to local blockchain
    
        truffle migrate


## Code Structure

    ├── blockchain-voting-dapp            # Root directory of the project.
        ├── build                         # Directory containing compiled contract artifacts.
        |   └── contracts                 
        |       ├── Migrations.json       
        |       └── Voting.json           
        ├── contracts                     # Directory containing smart contract source code.
        |   ├── 2_deploy_contracts.js     
        |   ├── Migrations.sol            
        |   └── Voting.sol                
        ├── Database_API                  # API code for database communication.
        |   └── main.py                   
        ├── migrations                    # Ethereum contract deployment scripts.
        |   └── 1_initial_migration.js    
        ├── node_modules                  # Node.js modules and dependencies.
        ├── public                        # Public assets like favicon.
        |   └── favicon.ico               
        ├── src                           
        |   ├── assets                    # Project images.
        |   |   └── eth5.jpg              
        |   ├── css                       # CSS stylesheets.
        |   |   ├── admin.css             
        |   |   ├── index.css             
        |   |   └── login.css             
        |   ├── dist                      # Compiled JavaScript bundles.
        |   |   ├── app.bundle.js         
        |   |   └── login.bundle.js       
        |   ├── html                      # HTML templates.
        |   |   ├── admin.html            
        |   |   ├── index.html            
        |   |   └── login.html            
        |   └── js                        # JavaScript logic files.
        |       ├── app.js                
        |       └── login.js              
        ├── index.js                      # Main entry point for Node.js application.
        ├── package.json                  # Node.js package configuration.
        ├── package-lock.json             # Lockfile for package dependencies.
        ├── README.md                     # Project documentation.
        └── truffle-config.js                    # Truffle configuration file.



