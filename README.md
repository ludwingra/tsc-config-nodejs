
# Typescript configuration for nodejs

> This is the configuration that worked best for me to work with typescript in nodejs, besides being easy to configure the debug


### Create project nodejs 
```
    npm init -y
````

### Install Typescript, ts-node and nodemon
```
    npm install -D typescript ts-node nodemon
````

### Create file tsconfig 
```
    tsc --init
````
* We make the following changes
    ````
        {
            "compilerOptions": {
                "target": "es6",
                "module": "commonjs",
                "outDir": "./dist",
                "rootDir": "./src",
                "strict": true,
                "moduleResolution": "node", 
                "esModuleInterop": true,
                "skipLibCheck": true,
                "forceConsistentCasingInFileNames": true
            },
            "include": [
                "./src/**/*"
            ],
            "exclude": [
                "node_modules"
            ]
        }

<hr>
### Create file nodemon 
```
    touch nodemon.json
````
* config nodemon file
    ````
        {
            "watch": [
                "src"
            ],
            "ext": "ts",
            "ignore": [
                "src/**/*.spec.ts"
            ],
            "exec": "ts-node ./src/index.ts"
        }


### Create script to run nodemo in development and start in production

* In the package.json file in the scripts we add
    ````
        "scripts": {
            "ts:node": "ts-node ./src/index.ts",
            "clean": "rm -r dist",
            "build": "tsc",
            "start": "node dist/",
            "dev": "nodemon"
        },

### Run environments
* Run development environment 
    ````
        npm run dev

* Run production environment 
    ````
        npm run build
        npm run start
