TypeScript With ts-node-dev
Sample commands to init a NodeJS TypeScript project

Dependencies
yarn add typescript ts-node ts-node-dev @types/node
OR

npm i typescript ts-node ts-node-dev @types/node
tsconfig.json
Create tsconfig.json in the root directory that will contain your typescript compiler configuration, more information in https://www.typescriptlang.org/docs/handbook/tsconfig-json.html

{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "outDir": "./dist",
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true,
    "esModuleInterop": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "**/*.test.ts"]
}
According to our configuration you should write your code in src/ folder and should have an entry point file called index.ts inside.

image

package.json
Add dev and build scripts to your package.json file,

Dev: Uses ts-node-dev to start a dev server that automatically transpiles your .ts files to .js whenever you edit something. (More info at https://www.npmjs.com/package/ts-node-dev)
Build: Uses tsc to transpile your whole application to .js, is used when you want to deploy to production. (More info at https://www.typescriptlang.org/docs/handbook/compiler-options.html)
"scripts": {
    "build": "tsc",
    "dev": "ts-node-dev --respawn --transpile-only src/index.ts"
  }
NPM Package
If you are writing a npm package specify main and types path and add --declaration to your build script in order to generate types suggestions to who is using your package.

package.json

"main" : "dist/index.js",
"types" : "dist/index.d.ts",
"scripts": {
    "build": "tsc --declaration"
  }
Run
npm run dev
OR

yarn dev
Build
npm run build
or

yarn build
