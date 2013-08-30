fs       = require 'fs'
UglifyJS = require 'uglify-js'
{exec}   = require 'child_process'

task 'build', 'Build project from *.coffee to *.js', ->
  exec 'coffee --compile number-polyfill.coffee spec.coffee', (err, stdout, stderr) ->
    throw err if err
    console.log stdout + stderr
    fs.writeFile 'number-polyfill.min.js', UglifyJS.minify('number-polyfill.js').code, 'utf8', (err) ->
      throw err if err
      console.log stdout + stderr
      exec 'sass number-polyfill.scss number-polyfill.css', (err, stdout, stderr) ->
        throw err if err
        console.log stdout + stderr
        console.log 'Done.'
