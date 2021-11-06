---
title: Webpack+React
date: 2021-11-06 12:28:14
categories: javascript
---

## Webpack + React

### 需要依赖

```shell
yarn add @babel/core @babel/preset-env @babel/preset-react babel-loader --dev

yarn add  webpack webpack-cli webpack-dev-server clean-webpack-plugin  html-webpack-plugin --dev

yarn add css-loader sass sass-loader style-loader --dev

yarn add react react-dom
```

### webpack.config.js

```js
const path = require('path')
const htmlWebpackPlugin = require('html-webpack-plugin')
const { CleanWebpackPlugin } = require('clean-webpack-plugin')

module.exports = {
  mode: 'development', //production development
  entry: path.join(__dirname, 'src', 'main.jsx'),
  output: {
    path: path.join(__dirname, 'dist'),
    filename: 'bundle.js',
    assetModuleFilename: 'images/[hash][ext][query]',
  },
  resolve: {
    extensions: ['.js', '.jsx', '.json'],
  },
  module: {
    rules: [
      {
        test: /\.(c|sc)ss$/,
        use: ['style-loader', 'css-loader', { loader: 'sass-loader' }],
      },
      {
        test: /\.(?:ico|gif|png|jpg|jpeg)$/i,
        type: 'asset/resource',
      },
      {
        test: /\.(js|jsx)$/,
        exclude: /(node_modules|bower_components)/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-env', '@babel/preset-react'],
          },
        },
      },
    ],
  },
  plugins: [
    new CleanWebpackPlugin(),
    new htmlWebpackPlugin({
      template: path.join(__dirname, 'public', 'index.html'),
      filename: 'index.html',
    }),
  ],
  devServer: {
    // compress: true,
    port: 3000,
  },
}
```

```shell
|-- node_modules
|-- public
	|-- index.html
|-- src
	|-- assets
	|-- main.jsx
|-- package.json
|-- webpack.config.js
```
