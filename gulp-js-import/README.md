## 说明
原插件gulp-js-import 没有识别相对路径，有可能会导致加载报错
修改原插件使之能识别相对路径

## INSTALL

```
npm install @webutf/gulp-js-import --save-dev
```
## USAGE

Then add it to the gulpfile.js:


```
var gulp = require('gulp');
var jsImport = require('@webutf/gulp-js-import');

gulp.task('import', function() {
  return gulp.src('index.js')
        .pipe(jsImport({hideConsole: true}))
        .pipe(gulp.dest('dist'));
});
```

Final, run import task where you need, eg: `gulp import`

### File Tree

this is the file tree:

```
demo
|
-- widget
|   |
|   -- widget.js
|   |
|   -- config.js
|   
-- index.js
|   
-- gulpfile.js
|   
-- package.json
```
### Brief Intorduce
index.js:


```
// index.js

@import './widget/widget.js'

output(config);

// index.js end
```

in `index.js`, you can use `@import 'xxx.js'` when you want import a js file

### Run

Enter the `demo` directory in command

```
cd demo
```
Install `gulp` `gulp-js-import` 

```
gulp install
```
Compile files

```
gulp import
```
You could see a js file `dist/index.js` like this:

```
// index.js
// widget.js
// config.js
var config = 'this is config value';
// config.js end

function output(str) {
  console.log(str);
}
// widget.js end

output(config);
// index.js end
```
