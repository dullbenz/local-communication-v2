# local_communication_app

> An electron-vue project

> Share files and messages between two computers on the same network

> Make sure to use node >= v14

#### Build Setup

``` bash
# install dependencies
yarn install

# serve with hot reload at localhost:9080
yarn dev

# build electron application for production
yarn build

# run unit & end-to-end tests
yarn test


# lint all JS/Vue component files in `src/`
yarn lint

```

---

#### Simple Usage Guide
When the app launches, on the first computer,
- Go to the listen tab
- Type a connection name and click listen

![Listen](https://github.com/dullbenz/local-communication-v2/raw/main/usage-images/Screenshot%20from%202022-11-23%2009-25-12.png)
On the second computer, 
- Go to the connect tab,
- Type the connection name
- Type the Ip address of the second computer
- Click connect

![Connect](https://github.com/dullbenz/local-communication-v2/blob/main/usage-images/Screenshot%20from%202022-11-23%2009-25-02.png)

You should now be able to share files and text between the two computers within the chat box that opens

This project was generated with [electron-vue](https://github.com/SimulatedGREG/electron-vue)@[8d4ed60](https://github.com/SimulatedGREG/electron-vue/tree/8d4ed607d65300381a8f47d97923eb07832b1a9a) using [vue-cli](https://github.com/vuejs/vue-cli). Documentation about the original structure can be found [here](https://simulatedgreg.gitbooks.io/electron-vue/content/index.html).
