This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `yarn start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `yarn eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (Webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `yarn build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify

项目中有遇到的坑：

1、cssnano 如果你的版本为：4+ 以上，请在配置中如下方案配置：

cssnano({
   "cssnano-preset-advanced": {
       zindex: false,
       autoprefixer: false
   },
})

我遇到了始终把你定位的z-index值重新计算为：1，巨坑，不然你会一口老血喷出来的。

和cssnano 3+版本配置不一样。


2、ios 系统下img不显示问题，解决方案如下：

/*兼容ios不显示图片问题*/
img {
   content: normal !important
}


3、1px 问题，解决方案

/*1px 解决方案*/

@svg square {
   @rect {
   	fill: var(--color, white);
   	width: 100%;
   	height: 50%;
   }
}

.example-line {
   width: 100%;
   background: white svg(square param(--color #E6E6E6));
   background-size: 100% 1px;
   background-repeat: no-repeat;
   background-position: bottom left;
}

/*1px 解决方案*/

/*伪元素1px*/

.row-cell:before {
   content: " ";
   position: absolute;
   left: 0;
   top: 0;
   right: 0;
   height: 1px;
   border-top: 1px solid #e5e5e5;
   color: #e5e5e5;
   transform-origin: 0 0;
   transform: scaleY(0.5);
   z-index: 2;
}