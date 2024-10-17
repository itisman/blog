# How to toggle the visibility of the left window?

Toggle the left window for the specific page

## Set class for some pages

> use /pages/my/my as example

```js
// App.vue
export default {
    // ...
    watch: {
        $route(to, from) {
            console.log(`from ${from.path} to ${to.path}`);
            // #ifdef H5
            const path = to?.path ?? location.hash.slice(1);

            if (path.indexOf("my") >= 0)
                setTimeout(() => {
                    document.body.classList.add("no-layout");
                });
            // #endif
        },
    },
};
```

## Hide left-window by CSS

```css
.no-layout {
    uni-top-window,
    uni-left-window,
    uni-right-window {
        display: none;
    }
}
```
