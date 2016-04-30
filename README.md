## gulp-sourcemaps  

--------------------------------------------------

This fork of gulp-sourcemaps has a prototype implementation of the `sourceLocation` sourcemap property via the 
`includePhysicalLocation` gulp-sourcemaps option. It's documented just below.

For all other documentation and production use, view the original [floridoo/gulp-sourcemaps](https://github.com/floridoo/gulp-sourcemaps). 

---------------------------------------------------

### Usage

To use this fork, you have two options:

##### Clone and link
```sh
git clone https://github.com/paulirish/gulp-sourcemaps/
cd gulp-sourcemaps
npm link

cd your-project-thats-using-gulp-sourcemaps
npm link gulp-sourcemaps
gulp build # or whatever it is
``` 

##### Depend on this fork

In your package.json, set this in your `devDependencies`:
```
    "gulp-sourcemaps": "github:paulirish/gulp-sourcemaps",
```

You can do set this in one line with: `npm install --save-dev paulirish/gulp-sourcemaps`

### Write Options

...

- `includePhysicalLocation`

  If you're using a tool that uses the physical location on disk of each file, this option adds all disk locations of each source into the source map.

  Example:
  ```javascript
  gulp.task('javascript', function() {
    var stream = gulp.src('src/**/*.js')
      .pipe(sourcemaps.init())
        .pipe(plugin1())
        .pipe(plugin2())
      .pipe(sourcemaps.write('.', {
        includePhysicalLocation: true
      }))
      .pipe(gulp.dest('public/scripts'));
  });
  ```
  Output:
  ```json
  {
    "version": 3,
    "file": "main.css",
    "sources": [
      "normalize.scss",
      "main.css",
      "root.scss",
      "_theme.scss",
      "main.scss"
    ],
    "sourceLocation": [
      "/Users/username/code/goweb/scss/normalize.scss",
      "/Users/username/code/goweb/scss/main.css",
      "/Users/username/code/goweb/scss/root.scss",
      "/Users/username/code/goweb/scss/_theme.scss",
      "/Users/username/code/goweb/scss/main.scss"
    ],
    "names": [],
    "mappings": "/* ... */",  
    "sourcesContent": "/* ... */",
  }
  ```
  