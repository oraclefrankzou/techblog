                  如何在vue项目中引入bootstrap

1,在项目目录中安装jquery,propper.js和bootstrap;

npm install jquery --save

npm install popper.js --save

npm install bootstrap --save


2,在webpack.base.conf.js中加载jquery plugin;

const webpack=require('webpack')

  plugins: [
    new webpack.ProvidePlugin({
      $: "jquery",
      jQuery: "jquery"
    })
  ],

3,在main.js中引入jquery和bootstrap;

import $ from 'jquery'
import 'bootstrap/dist/css/bootstrap.min.css'
import 'bootstrap/dist/js/bootstrap.min'
