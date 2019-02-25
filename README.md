# --async

> babel 6 demo is on babel6 branch

Browser list:

```
const browsers = [
  'last 1 Chrome versions',
  'last 1 Firefox versions',
  'last 1 Safari versions'
];
```

output

```js
;define("--async/routes/application", ["exports", "fetch"], function (_exports, _fetch) {
  "use strict";

  Object.defineProperty(_exports, "__esModule", {
    value: true
  });
  _exports.default = void 0;

  var _default = Ember.Route.extend({
    async model() {
      const result = await (0, _fetch.default)('/data.json');
      const json = await result.json();
      return await Ember.RSVP.Promise.resolve(json.data);
    }

  });

  _exports.default = _default;
});
```

Browser list

```js
const browsers = [
  'last 1 edge versions',
  'last 1 Chrome versions',
  'last 1 Firefox versions',
  'last 1 Safari versions',
  'ie 11'
];
```

```js
;define("--async/routes/application", ["exports", "ember-async-to-generator", "fetch"], function (_exports, _emberAsyncToGenerator, _fetch) {
  "use strict";

  Object.defineProperty(_exports, "__esModule", {
    value: true
  });
  _exports.default = void 0;

  var _default = Ember.Route.extend({
    model: function model() {
      return (0, _emberAsyncToGenerator.asyncToGenerator)(
      /*#__PURE__*/
      regeneratorRuntime.mark(function _callee() {
        var result, json;
        return regeneratorRuntime.wrap(function _callee$(_context) {
          while (1) {
            switch (_context.prev = _context.next) {
              case 0:
                _context.next = 2;
                return (0, _fetch.default)('/data.json');

              case 2:
                result = _context.sent;
                _context.next = 5;
                return result.json();

              case 5:
                json = _context.sent;
                _context.next = 8;
                return Ember.RSVP.Promise.resolve(json.data);

              case 8:
                return _context.abrupt("return", _context.sent);

              case 9:
              case "end":
                return _context.stop();
            }
          }
        }, _callee, this);
      }))();
    }
  });

  _exports.default = _default;
});
```