Components allow you to define controls that you can reuse throughout
your application. If they're generic enough, they can also be shared
with others and used in multiple applications.

To make a reusable control useful, however, you first need to allow
users of your application to interact with it.

You can make elements in your component interactive by using the
`{{action}}` helper. This is the [same `{{action}}` helper you use in
application templates](../../templates/actions), but it has an
important difference when used inside a component.

Instead of sending an action to the template's controller, then bubbling
up the route hierarchy, actions sent from inside a component are sent
directly to the component's `Ember.Component` instance, and do not
bubble.

For example, imagine the following component that shows a post's title.
When the title is clicked, the entire post body is shown:

```app/templates/components/post-summary.hbs
<h3 {{action "toggleBody"}}>{{title}}</h3>
{{#if isShowingBody}}
  <p>{{{body}}}</p>
{{/if}}
```

```app/components/post-summary.js
export default Ember.Component.extend({
  actions: {
    toggleBody() {
      this.toggleProperty('isShowingBody');
    }
  }
});
```

The `{{action}}` helper can accept arguments, listen for different event
types, control how action bubbling occurs, and more.

For details about using the `{{action}}` helper, see the [Actions
section](../../templates/actions) of the Templates chapter.
