# VueJS Resources
A big ol' list of VueJS stuff

**Note:** I'm pretty new to this whole testing thing so somethings might not be the correct way to do things, but I've just given it a go. If you are more experiences please fork this and edit the examples.

## <a name="table-of-contents"></a>Table of contents

* [Unit Testing](#unit-testing)
* [Vuex Unit Testing](#vuex-unit-testing)


## Great resources

* [Testing Vuex-Dependent Vue.js Components](https://alligator.io/vuejs/testing-vuex-vue/)
* [VueJS unit tests](https://github.com/vuejs/vue/tree/dev/test/unit/features/options)
* [Testing component props](https://vuejs.org/v2/guide/unit-testing.html#Writing-Testable-Components)
* [Testing component data](https://alligator.io/vuejs/unit-testing-karma-mocha/)
* [Testing with Mocks](https://github.com/vuejs/vue-loader/blob/master/docs/en/workflow/testing-with-mocks.md)
* [Testing with Mocks with Avoriaz](https://www.coding123.org/mock-vuex-in-vue-unit-tests/)
* [Testing language example](https://github.com/cbrown-tribpub/karma-browserify-vuejs/blob/master/tests/example.spec.js)



## <a id="unit-testing"></a>Unit Testing

I find testing Vue components super hard to test.

* [Testing example](https://gist.github.com/roberthamel/670640351ccac7a63630ec8b68537455)
* [VueJS Unit Testing](https://vuejs.org/v2/guide/unit-testing.html)
* [Slides on Unit Testing (tricky to understand)](https://www.slideshare.net/coulix/vuejs-testing)

## <a id="vuex-unit-testing"></a>Vuex Unit Testing
If found that Vuex is way easier to test that doing Vue components.

* [Vuex Unit testing](https://vuex.vuejs.org/en/testing.html)


* [Globally access styles - alias](https://github.com/vuejs/vue-loader/issues/328)

## Examples
* [White label app - ReactJS](https://github.com/hazmi/white-label-app)

## Webpack
* [Using Scss in VueJS 2](https://medium.com/@mahesh.ks/using-sass-scss-in-vue-js-2-d472af0facf9)
* [Globally access styles - alias](https://github.com/keydone/newBlog/blob/develop/build/webpack.base.conf.js)
* [Components with multiple themes](https://github.com/webpack/webpack/issues/1096)
* [How to extract multiple theme stylesheets with webpack?](http://stackoverflow.com/questions/38383889/how-to-extract-multiple-theme-stylesheets-with-webpack)

## Misc
* [Sass theming](https://webdesign.tutsplus.com/tutorials/how-to-use-sass-to-build-one-project-with-multiple-themes--cms-22104)


## Examples 

### Inspect the raw component options

```javascript 
export default {
 name: 'myComponent',
 data () {
  return {
   message: 'hello!'
  }
 },
 created () {
  this.message = 'bye!'
 }
}
```

```javascript
// Import Vue and the component being tested
import Vue from 'vue'
import MyComponent from 'path/to/MyComponent.vue'
// Here are some Jasmine 2.0 tests, though you can
// use any test runner / assertion library combo you prefer
describe('MyComponent', () => {
  // Inspect the raw component options
  it('has a created hook', () => {
    expect(typeof MyComponent.created).toBe('function')
  })
  // Evaluate the results of functions in
  // the raw component options
  it('sets the correct default data', () => {
    expect(typeof MyComponent.data).toBe('function')
    const defaultData = MyComponent.data()
    expect(defaultData.message).toBe('hello!')
  })
  // Inspect the component instance on mount
  it('correctly sets the message when created', () => {
    const vm = new Vue(MyComponent).$mount()
    expect(vm.message).toBe('bye!')
  })
  // Mount an instance and inspect the render output
  it('renders the correct message', () => {
    const Ctor = Vue.extend(MyComponent)
    const vm = new Ctor().$mount()
    expect(vm.$el.textContent).toBe('bye!')
  })
})
```
