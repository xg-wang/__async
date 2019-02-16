# --async

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