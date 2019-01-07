## CSS-in-JS? But why?  https://slides.com/kentcdodds/concerning-css-in-js
### And does it make sense to use it with Tailwind??

### Questions to ask when looking at a new CSS code:
1. Conventions
2. Who's using these styles? What's going to be affected? What impact will my change have elsewhere???
3. Can I delete these styles?
4. Where's the style for this particular div?

### The Pit of Success:
"A well designed system makes it easy to do the right things and annoying (but not impossible) to do the wrong things"

### Components
**What is a UI component made of?**

HTML/CSS/JS, that's right!

Uptil now, we have been colocating HTML and JS (with JSX), but what about CSS?
CSS is also a part of the UI component, so it makes sense to colocate them with HTML and JS, doesn't it?

If we can colocate CSS with JSX (HTML + JS), then we would have an absolute independent component in our hands. Isn't that amazing???
HTML, CSS and JS will exist in co-location 😉

And wait!!!

Exact! Explicit! WYSIWYG! Perfect!

In places, we can also take values from the global styles, but that would be only for those things that we define, and not others.

You are in JavaScript land! You can do anything that you can do with JS!!!

```javascript
const Button = styled(button)({
  display: 'inline-block',
  fontWeight: '400',
  color: '#f00',
  backgroundColor: '#025721',
});

const highlightStyles = {
  backgroundColor: '#025aa5',
  borderColor: '#01549b',
};

const PrimaryButton = styled(Button)(
  {  
    color: '#00f',
    backgroundColor: '#025768',
  },
  ({ active }) => (active ? highlightStyles : null)
);
```

### Utility classes of Tailwind can actually help us in this.

```
  Put an example in here with emotion (converting netlify UI to use emotion)
```

Scoped, isolated, specificity, Linting (we can simply use ESLint)

#### Jest Snapshots

We can take snapshots of the components styling through Jest and if we change something, you'd think that the JS file that contains the styling would show that the test failed in that, but no, it's actually the file that's using this style has a test that breaks.

You can now have all of the components in your application snapshotted!
So if you make a change to your CSS, you can actually see the impact of that change everywhere, in simple words, all of the tests will fail that concern to that CSS change. 

you can simply update the snapshots if everything seems fine and commit it :), another awesome features provided by Jest OUT OF THE BOX!!

How would you do it with CSS, is you'd need to run the tests by opening a headless browser and then all of that, which can take a lot of unnecessary time.

We just using composability with the components that we have :))

#### Automatic vendor prefixing

#### Concerns??

1. Familiarity
2. Workflow/IDE: autocompletion for CSS-in-JS? ESLint for rules? like display: nun? Checkout Kent C. Dodds plugin for this
3. Performance: 
Steps are -> 
With CSS-in-JS: Load JS -> Parse JS -> Run JS -> Generate CSS -> Inject CSS -> Parse CSS -> Apply CSS
With CSS, SASS: Load CSS -> Parse CSS -> Apply CSS
With Tailwind: Analyse??
With Tailwind + CSS-in-JS: Analyse??

How can we improve:
CSS-in-JS precompiler
glam
babel-plugin-styled-components
babel-plugin-polished
prepack

### Random questions of which I don't know the answers

1. Is CSS-in-JS fast as compared to simple CSS?

2. Benefits of using CSS-in-JS with tailwind? an example would be just perfect!!

3. Which styles do get inherited while using normal CSS, and why is that a problem? How does it get resolved while using CSS-in-JS? go in depth about this!!

4. Explore emotion

5. Do we apply all the styles??

6. How to apply tailwind utilities??