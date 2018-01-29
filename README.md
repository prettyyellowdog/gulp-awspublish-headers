# gulp-awspublish-headers

A plugin for defining per-file headers for [gulp-awspublish](https://github.com/pgherveou/gulp-awspublish).

## Usage

```js
const awsheaders = require('gulp-awspublish-headers');

gulp.task('publish', function() {
	const publisher = awspublish.create(/*...*/);

	return gulp.src('./public/**/*')
		.pipe(awsheaders({
			'path/to/**/*': {
				'Cache-Control': 'public, max-age=604800',
				'x-amz-meta-foo': 'bar',
			},
		}))
		.pipe(publisher.publish());
});
```

Files may match multiple paths in which case the headers will be merged with the later defined headers taking precedence.

## Installation

This is a [Node.js](https://nodejs.org/) module available through the 
[npm registry](https://www.npmjs.com/). It can be installed using the 
[`npm`](https://docs.npmjs.com/getting-started/installing-npm-packages-locally)
or 
[`yarn`](https://yarnpkg.com/en/)
command line tools.

```sh
npm install gulp-awspublish-headers --save
```

## Dependencies

- [minimatch](https://ghub.io/minimatch): a glob matcher in javascript
- [through2](https://ghub.io/through2): A tiny wrapper around Node streams2 Transform to avoid explicit subclassing noise

## License

BSD-3-Clause
