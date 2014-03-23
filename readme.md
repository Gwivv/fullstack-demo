# Fullstack demo generated using [Angular Fullstack][1]

[Angular Fullstack][1] is a MEAN generator. It scaffolds applications with MongoDB, Express, AngularJS, and Node. 

By running `yo angular-fullstack` and checking yes to everything, you get a project very similar to this. This repo is to give you an idea of what that project looks like.

## Getting Started

See original repository here: https://github.com/DaftMonk/fullstack-demo

## Replacing Compass by Stylus / Nib

Stylus is an Expressive, robust, feature-rich CSS preprocessor : http://learnboost.github.io/stylus/.

And Nib provide vendor support and others awesome functions : http://visionmedia.github.io/nib/.

Tasks performed :

 * [package.json][2] Remove unused dependencies and add Stylus dependencies needed.

      ```
      // "grunt-contrib-compass": "~0.6.0",
      "grunt-contrib-stylus": "~0.12.0",
      "stylus": "~0.42.2",
      "nib": "~1.0.2",
      "fluidity": "~0.2.0"
      ```

 * [Gruntfile.js][3] Remove Compass tasks and replace by Stylus tasks.

      ```
      ... [Watch task]
      stylus: {
        files: ['<%= yeoman.app %>/styles/**/*.styl'],
        tasks: ['stylus:server', 'autoprefixer']
      },
      ...
      ```

      ```
      ... [Stylus task]
      stylus: {
        compile: {
            options: {
                paths: ['<%= yeoman.app %>/styles/**/*.styl'],
                use: [
                    require('fluidity'), // use stylus plugin at compile time
                    require('nib')
                ],
                import: [
                    'nib',
                    '../function'
                ]
            },
            files: {
                '.tmp/styles/main.css':['<%= yeoman.app %>/styles/main.styl']
            }
        }
      },
      ...
      ```

 * [main.styl][4] Rename of main.scss in main.styl and refactor code.

      ```
      /* define color variable */
      $border-color=#e5e5e5
      /* and use it like this */
      .header
        border-bottom 1px solid $border-color
      ```

 * [bower.json][5] Add bootstrap-css-only component instead of compass import bootstrap.

      ```
      // "sass-bootstrap": "~3.0.2",
      "bootstrap-css-only": "~3.0.0",
      ```

 * [index.html][6] Replace import css of sass-bootstrap by bootstrap-css-only.

      ```
      <!--link rel="stylesheet" href="bower_components/sass-bootstrap/dist/css/bootstrap.css" /-->
      <link rel="stylesheet" href="bower_components/bootstrap-css-only/css/bootstrap.css" />
      ```

# Performed also changes :

 * To use the awesome 404 page provide by google even with your local node.js server, replace all ```res.send(404)``` line like this :

      ```
      // res.send(404);
      res.render("404.html");
      ```

 * [routes.js][7] Add route for undefined api path requested :

      ```
      app.get('/api/*', function(req, res) {
          res.render("404.html");
      });
      ```

# Simple way to start it :

 * Install node.js, grunt, bower, yeoman and mongodb then do in project folder :

      ```
      sudo npm install
      bower install
      grunt serve or grunt serve:dist
      ```

 * [gyp issue][8] In case of issue with bcrypt module, try to do this :

      ```
      sudo apt-get remove gyp
      sudo npm install node-expat
      ```

  [1]: https://github.com/DaftMonk/generator-angular-fullstack
  [2]: https://github.com/Gwivv/fullstack-demo/blob/master/package.json
  [3]: https://github.com/Gwivv/fullstack-demo/blob/master/Gruntfile.js
  [4]: https://github.com/Gwivv/fullstack-demo/blob/master/app/styles/main.styl
  [5]: https://github.com/Gwivv/fullstack-demo/blob/master/bower.json
  [6]: https://github.com/Gwivv/fullstack-demo/blob/master/app/views/index.html
  [7]: https://github.com/Gwivv/fullstack-demo/blob/master/lib/routes.js
  [8]: https://github.com/TooTallNate/node-gyp/issues/363