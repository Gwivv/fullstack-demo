# Fullstack demo generated using [Angular Fullstack][1]

[Angular Fullstack][1] is a MEAN generator. It scaffolds applications with MongoDB, Express, AngularJS, and Node. 

By running `yo angular-fullstack` and checking yes to everything, you get a project very similar to this. This repo is to give you an idea of what that project looks like.

## Getting Started

See original repository here: https://github.com/DaftMonk/fullstack-demo

## Replace Compass/Less by Stylus/Nib Install

Tasks performed :

 * [package.json][2] Remove unused dependencies and add Stylus dependencies needed.

      --"grunt-contrib-compass": "~0.6.0",--
      "grunt-contrib-stylus": "~0.12.0",
      "stylus": "~0.42.2",
      "nib": "~1.0.2",
      "fluidity": "~0.2.0"

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
 * [bower.json][5] Add bootstrap-css-only component instead of compass import bootstrap.


  [1]: https://github.com/DaftMonk/generator-angular-fullstack
  [2]: https://github.com/Gwivv/fullstack-demo/blob/master/package.json
  [3]: https://github.com/Gwivv/fullstack-demo/blob/master/Gruntfile.js
  [4]: https://github.com/Gwivv/fullstack-demo/blob/master/app/styles/main.styl
  [5]: https://github.com/Gwivv/fullstack-demo/blob/master/bower.json