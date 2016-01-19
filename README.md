# gulp-flow-livereload

[Livereload](https://github.com/vohof/gulp-livereload) bundle for [gulp-flow](https://github.com/gulp-flow/gulp-flow).


## Requirements

 * [gulp-flow](https://github.com/gulp-flow/gulp-flow) must be installed.


## Install

```sh
npm install --save-dev gulp-flow-livereload
```


## Usage

A simple example:

_gulpfile.js_
```js
let gulp = require('gulp');
let flow = require('gulp-flow');
let {cfg, gp} = flow;

// load the livereload bundle
require('gulp-flow-livereload');

// just for an example in the real word,
// load (custom) webpack bundle
require('./tasks/bundles/webpack');


gulp.task('local.build.webpack', function() {
  return gulp.src(cfg.webpack.entry.main)
    .pipe(gp.webpack(cfg.webpack))
    .pipe(gulp.dest(cfg.publicJsDir))
    .pipe(gp.livereload())
  ;
});

gulp.task('local.watch', function(done) {
  gp.livereload.listen();
  gulp.watch('./src/**/*.{js,jsx}', gulp.series('local.build.webpack'));

  done();
});
```

Now, browser page is refreshed when the task `local.build.webpack` is executed.

See [gulp-livereload](https://github.com/vohof/gulp-livereload) for more details.


## LICENSE

[MIT](https://github.com/gulp-flow/gulp-flow-livereload/blob/master/LICENSE) (c) 2016, Nicolas Tallefourtane.


## Author

| [![Nicolas Tallefourtane - Nicolab.net](http://www.gravatar.com/avatar/d7dd0f4769f3aa48a3ecb308f0b457fc?s=64)](http://nicolab.net) |
|---|
| [Nicolas Talle](http://nicolab.net) |
| [![Make a donation via Paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=PGRH4ZXP36GUC) |