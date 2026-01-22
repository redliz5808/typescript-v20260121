# Welcome to my first *Official* TypeScript Project

This is my first official TypeScript Project. I'm working from scratch just to get familiar with the syntax. It'll be a basic single-page application displaying minimal information and requiring minimal interaction from the user.

## Running the Application Locally
Note: The following assumes that you have cloned the repository to your local machine as well as have the following installed:
- [Node](https://nodejs.org/en)
- [Typescript](https://www.typescriptlang.org/download/)

### Initialize Typescript
```
tsc --init
```

### Compile Typescript
```
tsc
```

Note: If ```compilerOptions``` are not configured correctly under ```tsconfig.json```, you will need to run the following command instead:
```
tsc index.ts
```

## Notes
### Considerations: tsconfig.json
- **```compilerOptions``` → ```rootDir```**: This option defines which directory will contain the TS files to be compiled.
- **```compilerOptions``` → ```outDir```**: This option defines which directory will contain the JS files once compiled.
- **```compilerOptions``` → ```removeComments```**: If set to true, comments will not be included upon compiling.
    - Default setting: false (but not included in tsconfig.json)
- **```compilerOptions``` → ```noEmitOnError```**: If set to true, JS files will not be created if an type checking errors are reporting upon compiling.
    - Default setting: false (but not included in tsconfig.json)

### Initializing Variables With and Without Types
- If a variable is initialized with a value, TS will assume the type matches the type of the value.
    - Example #1: In the following line, TS will assume the type of ```myNum``` is an number: 
    ```
    let myNum = 123;
    ```
    - Example #2: In the following line, TS will assume the type of ```myName``` is a string: 
    ```
    let myName = "John";
    ```
- If a veriable is initialized without a value, TS will assume the type is ```any```.
    - Example: In the following line, TS will assume the type of ```myVal``` is any: 
    ```
    let myVal;
    ```

### Debugging in VS Code
1. Make sure Source Mapping is enabled.
   1. Found under ```tsconfig.json``` → ```compilerOptions``` → ```sourceMap```.
2. Open the Run and Debug Menu.
3. Select "create a launch.json file.
4. Select Node.js from the dropdown.
5. Open launch.json and verify the ```configurations``` → ```program``` value is pointing to the correct location:
    1. Correct value for this project: ```${workspaceFolder}/src/index.ts```
6. Open launch.json and verify the ```configurations``` → ```outputFiles``` value is pointing to the correct location:
    1. Correct value for this project: ```${workspaceFolder}/**/*.js```
7. Add the following line under ```configurations``` and between ```program``` and ```outputFiles```:
```
"preLaunchTask": "tsc: build - tsconfig.json",
```
