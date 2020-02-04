## Creating Electron React Applicat

Guideline for creating electron with react applications.

1.  **npx create-react-app**  <app-name>

2. **cd** <app-name>

3. **npm install electron electron-builder wait-on concurrently --dev**

4. **npm install electron-is-dev**

5. **npm install electron-squirrel-startup**

6. navigate to **public** folder

7. create a file **electron.js**

8. open **package.json**

9. In Main Section Add **"main": "public/electron.js"**

10. In scripts section add **"electron-dev": "concurrently \"BROWSER=none npm run start\"  \"wait-on http://localhost:3000 && electron .\""**

11. copy paste following code in ** electron.js** file

12. ```js
    const { app, BrowserWindow, ipcMain } = require('electron');
    ```
    
    #### Userful Links
    
    1. **Building Guide:** [https://www.electron.build/](https://www.electron.build/)
    
    2. **Example Repo:** [https://github.com/kitze/react-electron-example](https://github.com/kitze/react-electron-example)
    
    3. **Guide Doc:** [https://medium.com/@kitze/%EF%B8%8F-from-react-to-an-electron-app-ready-for-production-a0468ecb1da3](https://medium.com/@kitze/%EF%B8%8F-from-react-to-an-electron-app-ready-for-production-a0468ecb1da3)

```js
// Handle creating/removing shortcuts on Windows when installing/uninstalling.
if (require('electron-squirrel-startup')) { // eslint-disable-line global-require
  app.quit();
}


const path = require('path');
const url = require('url');
const isDev = require('electron-is-dev');


// Keep a global reference of the window object, if you don't, the window will
// be closed automatically when the JavaScript object is garbage collected.
let mainWindow;

const createWindow = () => {
  mainWindow = new BrowserWindow({width: 900, height: 680, webPreferences: { nodeIntegration: true }});
  mainWindow.loadURL(isDev ? 'http://localhost:3000' : `file://${path.join(__dirname, '../build/index.html')}`);
  // Open the DevTools.
  mainWindow.webContents.openDevTools();

  // Emitted when the window is closed.
  mainWindow.on('closed', () => {
    // Dereference the window object, usually you would store windows
    // in an array if your app supports multi windows, this is the time
    // when you should delete the corresponding element.
    mainWindow = null;
  });
}

// This method will be called when Electron has finished
// initialization and is ready to create browser windows.
// Some APIs can only be used after this event occurs.
app.on('ready', createWindow);

// Quit when all windows are closed.
app.on('window-all-closed', () => {
  // On OS X it is common for applications and their menu bar
  // to stay active until the user quits explicitly with Cmd + Q
  if (process.platform !== 'darwin') {
    app.quit();
  }
});

app.on('activate', () => {
  // On OS X it's common to re-create a window in the app when the
  // dock icon is clicked and there are no other windows open.
  if (mainWindow === null) {
    createWindow();
  }
});

// In this file you can include the rest of your app's specific main process
// code. You can also put them in separate files and import them here.
```
