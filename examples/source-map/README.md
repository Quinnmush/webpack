This example demonstrates various types of source-maps.

# example.coffee

```coffeescript
# Taken from http://coffeescript.org/

# Objects:
math =
  root:   Math.sqrt
  square: square
  cube:   (x) -> x * square x

# Splats:
race = (winner, runners...) ->
  print winner, runners
```

# webpack.config.js

```javascript
var path = require("path");

module.exports = [
	"eval",
	"eval-cheap-source-map",
	"eval-cheap-module-source-map",
	"eval-source-map",
	"cheap-source-map",
	"cheap-module-source-map",
	"inline-cheap-source-map",
	"inline-cheap-module-source-map",
	"source-map",
	"inline-source-map",
	"hidden-source-map",
	"nosources-source-map"
].map(devtool => ({
	mode: "development",
	entry: {
		bundle: "coffee-loader!./example.coffee"
	},
	output: {
		path: path.join(__dirname, "dist"),
		filename: `./[name]-${devtool}.js`
	},
	devtool,
	optimization: {
		runtimeChunk: true
	}
}));
```

# Generated source-maps

## source-map.js and source-map.js.map

```javascript
(self["webpackChunk"] = self["webpackChunk"] || []).push([[0],[
/* 0 */
/***/ (() => {

// Taken from http://coffeescript.org/

// Objects:
var math, race;

math = {
  root: Math.sqrt,
  square: square,
  cube: function(x) {
    return x * square(x);
  }
};

// Splats:
race = function(winner, ...runners) {
  return print(winner, runners);
};


/***/ })
],
0,[[0,1]]]);
//# sourceMappingURL=bundle-source-map.js.map
```

```json
{"version":3,"sources":["webpack:///./example.coffee"],"names":[],"mappings":";;;;AAEU;;;AAAA;;AACV,OACE;EAAA,MAAQ,IAAI,CAAC,IAAb;EACA,QAAQ,MADR;EAEA,MAAQ,SAAC,CAAD;WAAO,IAAI,OAAO,CAAP;EAAX;AAFR,EAFQ;;;AAOV,OAAO,SAAC,MAAD,KAAS,OAAT;SACL,MAAM,MAAN,EAAc,OAAd;AADK","file":"./bundle-source-map.js","sourcesContent":["# Taken from http://coffeescript.org/\n\n# Objects:\nmath =\n  root:   Math.sqrt\n  square: square\n  cube:   (x) -> x * square x\n\n# Splats:\nrace = (winner, runners...) ->\n  print winner, runners\n"],"sourceRoot":""}
```

## hidden-source-map.js and hidden-source-map.js.map

```javascript
(self["webpackChunk"] = self["webpackChunk"] || []).push([[0],[
/* 0 */
/***/ (() => {

// Taken from http://coffeescript.org/

// Objects:
var math, race;

math = {
  root: Math.sqrt,
  square: square,
  cube: function(x) {
    return x * square(x);
  }
};

// Splats:
race = function(winner, ...runners) {
  return print(winner, runners);
};


/***/ })
],
0,[[0,1]]]);
```

```json
{"version":3,"sources":["webpack:///./example.coffee"],"names":[],"mappings":";;;;AAEU;;;AAAA;;AACV,OACE;EAAA,MAAQ,IAAI,CAAC,IAAb;EACA,QAAQ,MADR;EAEA,MAAQ,SAAC,CAAD;WAAO,IAAI,OAAO,CAAP;EAAX;AAFR,EAFQ;;;AAOV,OAAO,SAAC,MAAD,KAAS,OAAT;SACL,MAAM,MAAN,EAAc,OAAd;AADK","file":"./bundle-hidden-source-map.js","sourcesContent":["# Taken from http://coffeescript.org/\n\n# Objects:\nmath =\n  root:   Math.sqrt\n  square: square\n  cube:   (x) -> x * square x\n\n# Splats:\nrace = (winner, runners...) ->\n  print winner, runners\n"],"sourceRoot":""}
```

## inline-source-map.js

```javascript
(self["webpackChunk"] = self["webpackChunk"] || []).push([[0],[
/* 0 */
/***/ (() => {

// Taken from http://coffeescript.org/

// Objects:
var math, race;

math = {
  root: Math.sqrt,
  square: square,
  cube: function(x) {
    return x * square(x);
  }
};

// Splats:
race = function(winner, ...runners) {
  return print(winner, runners);
};


/***/ })
],
0,[[0,1]]]);
//# sourceMappingURL=data:application/json;charset=utf-8;base64,eyJ2ZXJzaW9uIjozLCJzb3VyY2VzIjpbIndlYnBhY2s6Ly8vLi9leGFtcGxlLmNvZmZlZSJdLCJuYW1lcyI6W10sIm1hcHBpbmdzIjoiOzs7O0FBRVU7OztBQUFBOztBQUNWLE9BQ0U7RUFBQSxNQUFRLElBQUksQ0FBQyxJQUFiO0VBQ0EsUUFBUSxNQURSO0VBRUEsTUFBUSxTQUFDLENBQUQ7V0FBTyxJQUFJLE9BQU8sQ0FBUDtFQUFYO0FBRlIsRUFGUTs7O0FBT1YsT0FBTyxTQUFDLE1BQUQsS0FBUyxPQUFUO1NBQ0wsTUFBTSxNQUFOLEVBQWMsT0FBZDtBQURLIiwiZmlsZSI6Ii4vYnVuZGxlLWlubGluZS1zb3VyY2UtbWFwLmpzIiwic291cmNlc0NvbnRlbnQiOlsiIyBUYWtlbiBmcm9tIGh0dHA6Ly9jb2ZmZWVzY3JpcHQub3JnL1xuXG4jIE9iamVjdHM6XG5tYXRoID1cbiAgcm9vdDogICBNYXRoLnNxcnRcbiAgc3F1YXJlOiBzcXVhcmVcbiAgY3ViZTogICAoeCkgLT4geCAqIHNxdWFyZSB4XG5cbiMgU3BsYXRzOlxucmFjZSA9ICh3aW5uZXIsIHJ1bm5lcnMuLi4pIC0+XG4gIHByaW50IHdpbm5lciwgcnVubmVyc1xuIl0sInNvdXJjZVJvb3QiOiIifQ==
```

## nosources-source-map.js.map

```json
{"version":3,"sources":["webpack:///./example.coffee"],"names":[],"mappings":";;;;AAEU;;;AAAA;;AACV,OACE;EAAA,MAAQ,IAAI,CAAC,IAAb;EACA,QAAQ,MADR;EAEA,MAAQ,SAAC,CAAD;WAAO,IAAI,OAAO,CAAP;EAAX;AAFR,EAFQ;;;AAOV,OAAO,SAAC,MAAD,KAAS,OAAT;SACL,MAAM,MAAN,EAAc,OAAd;AADK","file":"./bundle-nosources-source-map.js","sourceRoot":""}
```

## eval-source-map.js

```javascript
/*
 * ATTENTION: An "eval-source-map" devtool has been used.
 * This devtool is not neither made for production nor for readable output files.
 * It uses "eval()" calls to create a separate source file with attached SourceMaps in the browser devtools.
 * If you are trying to read the output file, select a different devtool (https://webpack.js.org/configuration/devtool/)
 * or disable the default devtool with "devtool: false".
 * If you are looking for production-ready output files, see mode: "production" (https://webpack.js.org/configuration/mode/).
 */
(self["webpackChunk"] = self["webpackChunk"] || []).push([[0],[
/* 0 */
/***/ (() => {

eval("// Taken from http://coffeescript.org/\n\n// Objects:\nvar math, race;\n\nmath = {\n  root: Math.sqrt,\n  square: square,\n  cube: function(x) {\n    return x * square(x);\n  }\n};\n\n// Splats:\nrace = function(winner, ...runners) {\n  return print(winner, runners);\n};\n//# sourceURL=[module]\n//# sourceMappingURL=data:application/json;charset=utf-8;base64,eyJ2ZXJzaW9uIjozLCJzb3VyY2VSb290IjoiIiwic291cmNlcyI6WyJ3ZWJwYWNrOi8vLy4vZXhhbXBsZS5jb2ZmZWU/MjQxNiJdLCJuYW1lcyI6W10sIm1hcHBpbmdzIjoiQUFFVTs7O0FBQUEsSUFBQSxJQUFBLEVBQUE7O0FBQ1YsSUFBQSxHQUNFO0VBQUEsSUFBQSxFQUFRLElBQUksQ0FBQyxJQUFiO0VBQ0EsTUFBQSxFQUFRLE1BRFI7RUFFQSxJQUFBLEVBQVEsUUFBQSxDQUFDLENBQUQsQ0FBQTtXQUFPLENBQUEsR0FBSSxNQUFBLENBQU8sQ0FBUDtFQUFYO0FBRlIsRUFGUTs7O0FBT1YsSUFBQSxHQUFPLFFBQUEsQ0FBQyxNQUFELEVBQUEsR0FBUyxPQUFULENBQUE7U0FDTCxLQUFBLENBQU0sTUFBTixFQUFjLE9BQWQ7QUFESyIsInNvdXJjZXNDb250ZW50IjpbIiMgVGFrZW4gZnJvbSBodHRwOi8vY29mZmVlc2NyaXB0Lm9yZy9cblxuIyBPYmplY3RzOlxubWF0aCA9XG4gIHJvb3Q6ICAgTWF0aC5zcXJ0XG4gIHNxdWFyZTogc3F1YXJlXG4gIGN1YmU6ICAgKHgpIC0+IHggKiBzcXVhcmUgeFxuXG4jIFNwbGF0czpcbnJhY2UgPSAod2lubmVyLCBydW5uZXJzLi4uKSAtPlxuICBwcmludCB3aW5uZXIsIHJ1bm5lcnNcbiJdLCJmaWxlIjoiMC5qcyJ9\n//# sourceURL=webpack-internal:///0\n");

/***/ })
],
0,[[0,1]]]);
```

## eval.js

```javascript
/*
 * ATTENTION: The "eval" devtool has been used (maybe by default in mode: "development").
 * This devtool is not neither made for production nor for readable output files.
 * It uses "eval()" calls to create a separate source file in the browser devtools.
 * If you are trying to read the output file, select a different devtool (https://webpack.js.org/configuration/devtool/)
 * or disable the default devtool with "devtool: false".
 * If you are looking for production-ready output files, see mode: "production" (https://webpack.js.org/configuration/mode/).
 */
(self["webpackChunk"] = self["webpackChunk"] || []).push([[0],[
/* 0 */
/***/ (() => {

eval("// Taken from http://coffeescript.org/\n\n// Objects:\nvar math, race;\n\nmath = {\n  root: Math.sqrt,\n  square: square,\n  cube: function(x) {\n    return x * square(x);\n  }\n};\n\n// Splats:\nrace = function(winner, ...runners) {\n  return print(winner, runners);\n};\n\n\n//# sourceURL=webpack:///./example.coffee?../../node_modules/coffee-loader/dist/cjs.js");

/***/ })
],
0,[[0,1]]]);
```

## eval-cheap-source-map.js

```javascript
/*
 * ATTENTION: An "eval-source-map" devtool has been used.
 * This devtool is not neither made for production nor for readable output files.
 * It uses "eval()" calls to create a separate source file with attached SourceMaps in the browser devtools.
 * If you are trying to read the output file, select a different devtool (https://webpack.js.org/configuration/devtool/)
 * or disable the default devtool with "devtool: false".
 * If you are looking for production-ready output files, see mode: "production" (https://webpack.js.org/configuration/mode/).
 */
(self["webpackChunk"] = self["webpackChunk"] || []).push([[0],[
/* 0 */
/***/ (() => {

eval("// Taken from http://coffeescript.org/\n\n// Objects:\nvar math, race;\n\nmath = {\n  root: Math.sqrt,\n  square: square,\n  cube: function(x) {\n    return x * square(x);\n  }\n};\n\n// Splats:\nrace = function(winner, ...runners) {\n  return print(winner, runners);\n};\n//# sourceURL=[module]\n//# sourceMappingURL=data:application/json;charset=utf-8;base64,eyJ2ZXJzaW9uIjozLCJmaWxlIjoiMC5qcyIsInNvdXJjZXMiOlsid2VicGFjazovLy8uL2V4YW1wbGUuY29mZmVlP2VlNTgiXSwic291cmNlc0NvbnRlbnQiOlsiLy8gVGFrZW4gZnJvbSBodHRwOi8vY29mZmVlc2NyaXB0Lm9yZy9cblxuLy8gT2JqZWN0czpcbnZhciBtYXRoLCByYWNlO1xuXG5tYXRoID0ge1xuICByb290OiBNYXRoLnNxcnQsXG4gIHNxdWFyZTogc3F1YXJlLFxuICBjdWJlOiBmdW5jdGlvbih4KSB7XG4gICAgcmV0dXJuIHggKiBzcXVhcmUoeCk7XG4gIH1cbn07XG5cbi8vIFNwbGF0czpcbnJhY2UgPSBmdW5jdGlvbih3aW5uZXIsIC4uLnJ1bm5lcnMpIHtcbiAgcmV0dXJuIHByaW50KHdpbm5lciwgcnVubmVycyk7XG59O1xuIl0sIm1hcHBpbmdzIjoiQUFBQTtBQUNBO0FBQ0E7QUFDQTtBQUNBO0FBQ0E7QUFDQTtBQUNBO0FBQ0E7QUFDQTtBQUNBO0FBQ0E7QUFDQTtBQUNBO0FBQ0E7QUFDQTtBQUNBOyIsInNvdXJjZVJvb3QiOiIifQ==\n//# sourceURL=webpack-internal:///0\n");

/***/ })
],
0,[[0,1]]]);
```

## eval-cheap-module-source-map.js

```javascript
/*
 * ATTENTION: An "eval-source-map" devtool has been used.
 * This devtool is not neither made for production nor for readable output files.
 * It uses "eval()" calls to create a separate source file with attached SourceMaps in the browser devtools.
 * If you are trying to read the output file, select a different devtool (https://webpack.js.org/configuration/devtool/)
 * or disable the default devtool with "devtool: false".
 * If you are looking for production-ready output files, see mode: "production" (https://webpack.js.org/configuration/mode/).
 */
(self["webpackChunk"] = self["webpackChunk"] || []).push([[0],[
/* 0 */
/***/ (() => {

eval("// Taken from http://coffeescript.org/\n\n// Objects:\nvar math, race;\n\nmath = {\n  root: Math.sqrt,\n  square: square,\n  cube: function(x) {\n    return x * square(x);\n  }\n};\n\n// Splats:\nrace = function(winner, ...runners) {\n  return print(winner, runners);\n};\n//# sourceURL=[module]\n//# sourceMappingURL=data:application/json;charset=utf-8;base64,eyJ2ZXJzaW9uIjozLCJzb3VyY2VSb290IjoiIiwic291cmNlcyI6WyJ3ZWJwYWNrOi8vLy4vZXhhbXBsZS5jb2ZmZWU/MjQxNiJdLCJuYW1lcyI6W10sIm1hcHBpbmdzIjoiQUFFVTs7O0FBQUEsSUFBQSxJQUFBLEVBQUE7O0FBQ1YsSUFBQSxHQUNFO0VBQUEsSUFBQSxFQUFRLElBQUksQ0FBQyxJQUFiO0VBQ0EsTUFBQSxFQUFRLE1BRFI7RUFFQSxJQUFBLEVBQVEsUUFBQSxDQUFDLENBQUQsQ0FBQTtXQUFPLENBQUEsR0FBSSxNQUFBLENBQU8sQ0FBUDtFQUFYO0FBRlIsRUFGUTs7O0FBT1YsSUFBQSxHQUFPLFFBQUEsQ0FBQyxNQUFELEVBQUEsR0FBUyxPQUFULENBQUE7U0FDTCxLQUFBLENBQU0sTUFBTixFQUFjLE9BQWQ7QUFESyIsInNvdXJjZXNDb250ZW50IjpbIiMgVGFrZW4gZnJvbSBodHRwOi8vY29mZmVlc2NyaXB0Lm9yZy9cblxuIyBPYmplY3RzOlxubWF0aCA9XG4gIHJvb3Q6ICAgTWF0aC5zcXJ0XG4gIHNxdWFyZTogc3F1YXJlXG4gIGN1YmU6ICAgKHgpIC0+IHggKiBzcXVhcmUgeFxuXG4jIFNwbGF0czpcbnJhY2UgPSAod2lubmVyLCBydW5uZXJzLi4uKSAtPlxuICBwcmludCB3aW5uZXIsIHJ1bm5lcnNcbiJdLCJmaWxlIjoiMC5qcyJ9\n//# sourceURL=webpack-internal:///0\n");

/***/ })
],
0,[[0,1]]]);
```

## cheap-module-source-map.js.map

```json
{"version":3,"file":"./bundle-cheap-module-source-map.js","sources":["webpack:///./example.coffee"],"sourcesContent":["# Taken from http://coffeescript.org/\n\n# Objects:\nmath =\n  root:   Math.sqrt\n  square: square\n  cube:   (x) -> x * square x\n\n# Splats:\nrace = (winner, runners...) ->\n  print winner, runners\n"],"mappings":";;;;AAEA;AACA;;AADA;AACA;AAAA;AACA;AACA;AACA;AAAA;AAAA;AAFA;AACA;;AAIA;AACA;AADA;AACA;AACA;A;;A","sourceRoot":""}
```

## cheap-source-map.js.map

```json
{"version":3,"file":"./bundle-cheap-source-map.js","sources":["webpack:///./example.coffee"],"sourcesContent":["// Taken from http://coffeescript.org/\n\n// Objects:\nvar math, race;\n\nmath = {\n  root: Math.sqrt,\n  square: square,\n  cube: function(x) {\n    return x * square(x);\n  }\n};\n\n// Splats:\nrace = function(winner, ...runners) {\n  return print(winner, runners);\n};\n"],"mappings":";;;;AAAA;AACA;AACA;AACA;AACA;AACA;AACA;AACA;AACA;AACA;AACA;AACA;AACA;AACA;AACA;AACA;AACA;AACA;AACA;A;;A","sourceRoot":""}
```

# webpack output

```
asset [1m[32m./runtime~bundle-eval.js[39m[22m 5.72 KiB [1m[32m[emitted][39m[22m (name: runtime~bundle)
asset [1m[32m./bundle-eval.js[39m[22m 1.03 KiB [1m[32m[emitted][39m[22m (name: bundle)
Entrypoint [1mbundle[39m[22m 6.75 KiB = [1m[32m./runtime~bundle-eval.js[39m[22m 5.72 KiB [1m[32m./bundle-eval.js[39m[22m 1.03 KiB
runtime modules 2.56 KiB 2 modules
../../node_modules/coffee-loader/dist/cjs.js![1m./example.coffee[39m[22m 256 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.0 compiled [1m[32msuccessfully[39m[22m

asset [1m[32m./runtime~bundle-eval-cheap-source-map.js[39m[22m 5.72 KiB [1m[32m[emitted][39m[22m (name: runtime~bundle)
asset [1m[32m./bundle-eval-cheap-source-map.js[39m[22m 1.69 KiB [1m[32m[emitted][39m[22m (name: bundle)
Entrypoint [1mbundle[39m[22m 7.41 KiB = [1m[32m./runtime~bundle-eval-cheap-source-map.js[39m[22m 5.72 KiB [1m[32m./bundle-eval-cheap-source-map.js[39m[22m 1.69 KiB
runtime modules 2.56 KiB 2 modules
../../node_modules/coffee-loader/dist/cjs.js![1m./example.coffee[39m[22m 256 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.0 compiled [1m[32msuccessfully[39m[22m

asset [1m[32m./runtime~bundle-eval-cheap-module-source-map.js[39m[22m 5.72 KiB [1m[32m[emitted][39m[22m (name: runtime~bundle)
asset [1m[32m./bundle-eval-cheap-module-source-map.js[39m[22m 1.83 KiB [1m[32m[emitted][39m[22m (name: bundle)
Entrypoint [1mbundle[39m[22m 7.55 KiB = [1m[32m./runtime~bundle-eval-cheap-module-source-map.js[39m[22m 5.72 KiB [1m[32m./bundle-eval-cheap-module-source-map.js[39m[22m 1.83 KiB
runtime modules 2.56 KiB 2 modules
../../node_modules/coffee-loader/dist/cjs.js![1m./example.coffee[39m[22m 256 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.0 compiled [1m[32msuccessfully[39m[22m

asset [1m[32m./runtime~bundle-eval-source-map.js[39m[22m 5.72 KiB [1m[32m[emitted][39m[22m (name: runtime~bundle)
asset [1m[32m./bundle-eval-source-map.js[39m[22m 1.83 KiB [1m[32m[emitted][39m[22m (name: bundle)
Entrypoint [1mbundle[39m[22m 7.55 KiB = [1m[32m./runtime~bundle-eval-source-map.js[39m[22m 5.72 KiB [1m[32m./bundle-eval-source-map.js[39m[22m 1.83 KiB
runtime modules 2.56 KiB 2 modules
../../node_modules/coffee-loader/dist/cjs.js![1m./example.coffee[39m[22m 256 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.0 compiled [1m[32msuccessfully[39m[22m

asset [1m[32m./runtime~bundle-cheap-source-map.js[39m[22m 5.23 KiB [1m[32m[emitted][39m[22m (name: runtime~bundle) 1 related asset
asset [1m[32m./bundle-cheap-source-map.js[39m[22m 422 bytes [1m[32m[emitted][39m[22m (name: bundle) 1 related asset
Entrypoint [1mbundle[39m[22m 5.64 KiB (5.01 KiB) = [1m[32m./runtime~bundle-cheap-source-map.js[39m[22m 5.23 KiB [1m[32m./bundle-cheap-source-map.js[39m[22m 422 bytes 2 auxiliary assets
runtime modules 2.56 KiB 2 modules
../../node_modules/coffee-loader/dist/cjs.js![1m./example.coffee[39m[22m 256 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.0 compiled [1m[32msuccessfully[39m[22m

asset [1m[32m./runtime~bundle-cheap-module-source-map.js[39m[22m 5.24 KiB [1m[32m[emitted][39m[22m (name: runtime~bundle) 1 related asset
asset [1m[32m./bundle-cheap-module-source-map.js[39m[22m 429 bytes [1m[32m[emitted][39m[22m (name: bundle) 1 related asset
Entrypoint [1mbundle[39m[22m 5.66 KiB (4.94 KiB) = [1m[32m./runtime~bundle-cheap-module-source-map.js[39m[22m 5.24 KiB [1m[32m./bundle-cheap-module-source-map.js[39m[22m 429 bytes 2 auxiliary assets
runtime modules 2.56 KiB 2 modules
../../node_modules/coffee-loader/dist/cjs.js![1m./example.coffee[39m[22m 256 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.0 compiled [1m[32msuccessfully[39m[22m

asset [1m[32m./runtime~bundle-inline-cheap-source-map.js[39m[22m 11.2 KiB [1m[32m[emitted][39m[22m (name: runtime~bundle)
asset [1m[32m./bundle-inline-cheap-source-map.js[39m[22m 1.11 KiB [1m[32m[emitted][39m[22m (name: bundle)
Entrypoint [1mbundle[39m[22m 12.4 KiB = [1m[32m./runtime~bundle-inline-cheap-source-map.js[39m[22m 11.2 KiB [1m[32m./bundle-inline-cheap-source-map.js[39m[22m 1.11 KiB
runtime modules 2.56 KiB 2 modules
../../node_modules/coffee-loader/dist/cjs.js![1m./example.coffee[39m[22m 256 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.0 compiled [1m[32msuccessfully[39m[22m

asset [1m[32m./runtime~bundle-inline-cheap-module-source-map.js[39m[22m 11.3 KiB [1m[32m[emitted][39m[22m (name: runtime~bundle)
asset [1m[32m./bundle-inline-cheap-module-source-map.js[39m[22m 1.02 KiB [1m[32m[emitted][39m[22m (name: bundle)
Entrypoint [1mbundle[39m[22m 12.3 KiB = [1m[32m./runtime~bundle-inline-cheap-module-source-map.js[39m[22m 11.3 KiB [1m[32m./bundle-inline-cheap-module-source-map.js[39m[22m 1.02 KiB
runtime modules 2.56 KiB 2 modules
../../node_modules/coffee-loader/dist/cjs.js![1m./example.coffee[39m[22m 256 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.0 compiled [1m[32msuccessfully[39m[22m

asset [1m[32m./runtime~bundle-source-map.js[39m[22m 5.22 KiB [1m[32m[emitted][39m[22m (name: runtime~bundle) 1 related asset
asset [1m[32m./bundle-source-map.js[39m[22m 416 bytes [1m[32m[emitted][39m[22m (name: bundle) 1 related asset
Entrypoint [1mbundle[39m[22m 5.63 KiB (5 KiB) = [1m[32m./runtime~bundle-source-map.js[39m[22m 5.22 KiB [1m[32m./bundle-source-map.js[39m[22m 416 bytes 2 auxiliary assets
runtime modules 2.56 KiB 2 modules
../../node_modules/coffee-loader/dist/cjs.js![1m./example.coffee[39m[22m 256 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.0 compiled [1m[32msuccessfully[39m[22m

asset [1m[32m./runtime~bundle-inline-source-map.js[39m[22m 11.2 KiB [1m[32m[emitted][39m[22m (name: runtime~bundle)
asset [1m[32m./bundle-inline-source-map.js[39m[22m 1.13 KiB [1m[32m[emitted][39m[22m (name: bundle)
Entrypoint [1mbundle[39m[22m 12.4 KiB = [1m[32m./runtime~bundle-inline-source-map.js[39m[22m 11.2 KiB [1m[32m./bundle-inline-source-map.js[39m[22m 1.13 KiB
runtime modules 2.56 KiB 2 modules
../../node_modules/coffee-loader/dist/cjs.js![1m./example.coffee[39m[22m 256 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.0 compiled [1m[32msuccessfully[39m[22m

asset [1m[32m./runtime~bundle-hidden-source-map.js[39m[22m 5.17 KiB [1m[32m[emitted][39m[22m (name: runtime~bundle) 1 related asset
asset [1m[32m./bundle-hidden-source-map.js[39m[22m 370 bytes [1m[32m[emitted][39m[22m (name: bundle) 1 related asset
Entrypoint [1mbundle[39m[22m 5.53 KiB (5.02 KiB) = [1m[32m./runtime~bundle-hidden-source-map.js[39m[22m 5.17 KiB [1m[32m./bundle-hidden-source-map.js[39m[22m 370 bytes 2 auxiliary assets
runtime modules 2.56 KiB 2 modules
../../node_modules/coffee-loader/dist/cjs.js![1m./example.coffee[39m[22m 256 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.0 compiled [1m[32msuccessfully[39m[22m

asset [1m[32m./runtime~bundle-nosources-source-map.js[39m[22m 5.23 KiB [1m[32m[emitted][39m[22m (name: runtime~bundle) 1 related asset
asset [1m[32m./bundle-nosources-source-map.js[39m[22m 426 bytes [1m[32m[emitted][39m[22m (name: bundle) 1 related asset
Entrypoint [1mbundle[39m[22m 5.65 KiB (1.15 KiB) = [1m[32m./runtime~bundle-nosources-source-map.js[39m[22m 5.23 KiB [1m[32m./bundle-nosources-source-map.js[39m[22m 426 bytes 2 auxiliary assets
runtime modules 2.56 KiB 2 modules
../../node_modules/coffee-loader/dist/cjs.js![1m./example.coffee[39m[22m 256 bytes [1m[33m[built][39m[22m [1m[33m[code generated][39m[22m
webpack 5.10.0 compiled [1m[32msuccessfully[39m[22m
```
