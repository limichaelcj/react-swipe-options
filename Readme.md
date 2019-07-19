# react-swipe-options

Add custom action buttons under your React components that are revealed by swiping.

## Usage
Simply wrap your component with the SwipeOptions component and your component will be swipeable, but you will need to define your own components to include in the `left` and `right` props.
```js
<SwipeOptions
  left={[ <LeftItem /> ]}
  right={[ <RightItem /> ]}
>
  <MyComponent />
</SwipeOptions>
```

### Required props
- `children`: one React element child.

### Optional props
- `left`: an array of React elements to display on the left when swiped.
- `right`: an array of React elements to display on the right when swiped.
- `onSwiping`: function to call during a swipe. This function will be called repeatedly.
- `onSwiped`: function to call on a completed swipe. Will only be called once upon completion of the swipe action.
- `delta`: The distance threshold of a swipe that is required for the onSwiping function to trigger. (`px`, default: `4`)
- `disableTouch`: Allow swipe tracking via touch. (`boolean`, default: `false`)
- `disableMouse`: Allow swipe tracking via mouse click. (`boolean`, default: `false`)
- `unitSize`: The size of the action components under the child component (`px`, default: `64`)
- `motionBuffer`: A ratio applied to the distance of a swipe to modify the displacement of the child element in relation to the distance covered by the swipe in pixels. A low ratio number is preferred to make the child element feel 'heavy' and responsive. (default: `0.1`)
- `snapZone`: This number represents the percent of displacement of the child element required for it to snap to an open position. Any displacement under this percent value of potential displacement will snap the child element back to its original position. (default: `0.7`)
- `pressable`: Allows visual feedback of the child element being pressed. (`boolean`, default: `false`)
- `disabled`: Determines whether swipe actions will be triggered. (`boolean`, default: `false`)

### Example
This MessagesList component will use the data passed to it via `props.messages` and render a list of messages, each with an archive action button on the left when swiped right, and reply and ignore action buttons on the right when swiped left.
```js
function MessageList(props){
  return (
    {
      props.messages.map(data => {
        <SwipeOptions
          active
          left={[<ArchiveButton />]}
          right={[<ReplyButton />, <IgnoreButton />]}
          disableMouse // optional
          pressable // optional
        >
          <Message data={data} />
        </SwipeOptions>
      })
    }
  );
}
```
