backbone-flash
==============

Creates a flash notification feature for backbone. This feature is built on the Backbone event system and is extensible for custom display and delivery. By default it will use an underscore template and Bootstrap styling for alert messages.

##Intialization
Upon application start-up you must call `initialize` to enable flash messaging. This will use the default configuration which attaches flash messages to the HTML body element and will use underscore templating.

```javascript
Backbone.Flash.initialize();
```

To override the default config, you can pass a config object to the initialize function with the following properties:
* `el` overrides the element the flash messages will be rendered into
* `template` is the template for rendering
* `stayDuraction` dictates in MS how long a message will be displayed before being removed

```javascript
Backbone.Flash.initialize({
  el: '#flashes',
  template: Handlebars.compile($("#template-flashview").html()),
  stayDuraction: 10000
})
```

##Usage

Usage is easy, simply trigger a `flash` event and pass in an object containing the message and type properties

```javascript
Backbone.trigger('flash', { message: 'Successfully did something!', type: 'success' });
```

You can also persist a message by including `persist: true` when triggering the event

```javascript
Backbone.trigger('flash', { message: 'You should address this thing', type: 'info' });
```

You can also override the default configuration for flash when triggering the event by passing a config object

```javascript
Backbone.trigger('flash', { message: 'Display in a sidebar', type: 'success' }, { el: $("#sidebar") });
```


