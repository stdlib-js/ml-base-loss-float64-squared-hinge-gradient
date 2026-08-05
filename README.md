<!--

@license Apache-2.0

Copyright (c) 2026 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# squaredHingeGradient

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Compute the [squared hinge loss gradient][squared-hinge-loss-gradient] with respect to a model parameter.

<section class="intro">

The [squared hinge loss gradient][squared-hinge-loss-gradient] is defined as

<!-- <equation class="equation" label="eq:squared_hinge_loss_gradient" align="center" raw="\frac{\partial \ell}{\partial w} = \begin{cases} -2y(t - yp)x & \text{if } yp \leq t \\ 0 & \text{otherwise} \end{cases}" alt="Equation for the squared hinge loss gradient."> -->

```math
\frac{\partial \ell}{\partial w} = \begin{cases} -2y(t - yp)x & \text{if } yp \leq t \\ 0 & \text{otherwise} \end{cases}
```

<!-- <div class="equation" align="center" data-raw-text="\frac{\partial \ell}{\partial w} = \begin{cases} -2y(t - yp)x &amp; \text{if } yp \leq t \\ 0 &amp; \text{otherwise} \end{cases}" data-equation="eq:squared_hinge_loss_gradient">
    <img src="https://cdn.jsdelivr.net/gh/stdlib-js/stdlib@e72895028e08bd5faa19a580deaf380c3ff38e42/lib/node_modules/@stdlib/ml/base/loss/float64/squared-hinge-gradient/docs/img/equation_squared_hinge_loss_gradient.svg" alt="Equation for the squared hinge loss gradient.">
    <br>
</div> -->

<!-- </equation> -->

</section>

<!-- /.intro -->

<section class="installation">

## Installation

```bash
npm install @stdlib/ml-base-loss-float64-squared-hinge-gradient
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var squaredHingeGradient = require( '@stdlib/ml-base-loss-float64-squared-hinge-gradient' );
```

#### squaredHingeGradient( x, t, y, p )

Computes the [squared hinge loss gradient][squared-hinge-loss-gradient] with respect to a model parameter.

```javascript
var v = squaredHingeGradient( 3.0, 1.0, 1.0, 0.782 );
// returns ~-1.308

v = squaredHingeGradient( -1.3, 1.0, 1.0, -0.999 );
// returns ~5.197
```

The function accepts the following arguments:

-   **x**: input value.
-   **t**: margin threshold.
-   **y**: true target value.
-   **p**: predicted value.

If any argument is `NaN`, the function returns `NaN`.

```javascript
var v = squaredHingeGradient( NaN, 1.0, 1.0, 0.782 );
// returns NaN

v = squaredHingeGradient( 1.0, 1.0, NaN, 0.782 );
// returns NaN

v = squaredHingeGradient( NaN, NaN, 1.0, 0.782 );
// returns NaN

v = squaredHingeGradient( NaN, NaN, NaN, NaN );
// returns NaN
```

If `y` is not +1 or -1, the function returns `NaN`.

```javascript
var v = squaredHingeGradient( 3.0, 1.0, -0.9, 1.0 );
// returns NaN

v = squaredHingeGradient( 2.4, 1.0, 0.453, 0.76 );
// returns NaN
```

</section>

<!-- /.usage -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var uniform = require( '@stdlib/random-array-uniform' );
var sample = require( '@stdlib/random-sample' );
var logEachMap = require( '@stdlib/console-log-each-map' );
var squaredHingeGradient = require( '@stdlib/ml-base-loss-float64-squared-hinge-gradient' );

var y = sample( [ -1.0, 1.0 ], {
    'size': 100
});
var opts = {
    'dtype': 'float64'
};
var x = uniform( 100, -100.0, 100.0, opts );
var t = uniform( 100, 0.0, 5.0, opts );
var p = uniform( 100, -5.0, 5.0, opts );

logEachMap( 'squaredHingeGradient(%0.4f, %0.4f, %0.4f, %0.4f) = %0.4f', x, t, y, p, squaredHingeGradient );
```

</section>

<!-- /.examples -->

<!-- C interface documentation. -->

* * *

<section class="c">

## C APIs

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- C usage documentation. -->

<section class="usage">

### Usage

```c
#include "stdlib/ml/base/loss/float64/squared_hinge_gradient.h"
```

#### stdlib_base_float64_squared_hinge_gradient( x, t, y, p )

Computes the [squared hinge loss gradient][squared-hinge-loss-gradient] with respect to a model parameter.

```c
double out = stdlib_base_float64_squared_hinge_gradient( 3.0, 1.0, 1.0, 0.782 );
// returns ~-1.308
```

The function accepts the following arguments:

-   **x**: `[in] double` input value.
-   **t**: `[in] double` margin threshold.
-   **y**: `[in] double` true target value.
-   **p**: `[in] double` predicted value.

```c
double stdlib_base_float64_squared_hinge_gradient( const double x, const double t, const double y, const double p );
```

</section>

<!-- /.usage -->

<!-- C API usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- C API usage examples. -->

<section class="examples">

### Examples

```c
#include "stdlib/ml/base/loss/float64/squared_hinge_gradient.h"
#include <stdio.h>

int main( void ) {
    const double x[] = { -10.0, -9.56, -8.67, -7.78, -6.89, 6.89, 7.78, 8.67, 9.56, 10.0 };
    const double t[] = { 0.0, 1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0 };
    const double y[] = { -1.0, -1.0, -1.0, -1.0, -1.0, 1.0, 1.0, 1.0, 1.0, 1.0 };
    const double p[] = { -5.0, -3.89, -2.78, -1.67, -0.56, 0.56, 1.67, 2.78, 3.89, 5.0 };

    double v;
    int i;
    for ( i = 0; i < 10; i++ ) {
        v = stdlib_base_float64_squared_hinge_gradient( x[ i ], t[ i ], y[ i ], p[ i ] );
        printf( "squaredHingeGradient(%lf, %lf, %lf, %lf) = %lf\n", x[ i ], t[ i ], y[ i ], p[ i ], v );
    }
}
```

</section>

<!-- /.examples -->

</section>

<!-- /.c -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/ml-base-loss-float64-squared-hinge-gradient.svg
[npm-url]: https://npmjs.org/package/@stdlib/ml-base-loss-float64-squared-hinge-gradient

[test-image]: https://github.com/stdlib-js/ml-base-loss-float64-squared-hinge-gradient/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/ml-base-loss-float64-squared-hinge-gradient/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/ml-base-loss-float64-squared-hinge-gradient/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/ml-base-loss-float64-squared-hinge-gradient?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/ml-base-loss-float64-squared-hinge-gradient.svg
[dependencies-url]: https://david-dm.org/stdlib-js/ml-base-loss-float64-squared-hinge-gradient/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/ml-base-loss-float64-squared-hinge-gradient/tree/deno
[deno-readme]: https://github.com/stdlib-js/ml-base-loss-float64-squared-hinge-gradient/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/ml-base-loss-float64-squared-hinge-gradient/tree/umd
[umd-readme]: https://github.com/stdlib-js/ml-base-loss-float64-squared-hinge-gradient/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/ml-base-loss-float64-squared-hinge-gradient/tree/esm
[esm-readme]: https://github.com/stdlib-js/ml-base-loss-float64-squared-hinge-gradient/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/ml-base-loss-float64-squared-hinge-gradient/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/ml-base-loss-float64-squared-hinge-gradient/main/LICENSE

[squared-hinge-loss-gradient]: https://en.wikipedia.org/wiki/Hinge_loss#Optimization

<!-- <related-links> -->

<!-- </related-links> -->

</section>

<!-- /.links -->
