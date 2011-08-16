fs            = require 'fs'
{spawn, exec} = require 'child_process'

# Run a CoffeeScript through our node/coffee interpreter.
run = (args, cb) ->
  proc =         spawn 'coffee', args
  proc.stderr.on 'data', (buffer) -> console.log buffer.toString()
  proc.on        'exit', (status) ->
    process.exit(1) if status != 0
    cb() if typeof cb is 'function'


task 'build', 'build', build = (cb) ->
  files = fs.readdirSync '.'
  files = (file for file in files when file.match(/\.coffee$/))
  run ['-c'].concat(files), cb
