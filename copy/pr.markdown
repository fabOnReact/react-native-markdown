<!-- Thanks for submitting a pull request! We appreciate you spending the time to work on these changes. Please provide enough information so that others can review your pull request. The three fields below are mandatory. -->

## Summary

<!-- Explain the **motivation** for making this change. What existing problem does the pull request solve? -->

This issue fixes https://github.com/facebook/react-native/issues/30944 ([Test Case 7.1][7.1], [Test Case 7.3][7.3], [Test Case 7.5][7.5]) .
The issue is caused by the missing prop `accessibilityState` in the Text component.

The solution consists of passing the accessibilityState to the `AndroidTextNativeComponent` component as previously implemented in other components (for example, [Button][8]). 

Relevant discussions https://github.com/facebook/react-native/issues/30840#issuecomment-780981316 and https://github.com/facebook/react-native/pull/31001/files#r578827409.

[8]: https://github.com/facebook/react-native/pull/31224/files#diff-ab227579e3dfe69ff9b4952a09cf8ae78783e6fd9c2820f3c038e02c7406a6cdR171

The solution proposed in this pull request consists of:
1. Passing `accessibilityState` to the `AndroidTextNativeComponent`
2. If the value of prop `accessibilityState.disabled` is different from the prop `disabled`, the prop `disabled` over-rides the `accessibilityState.disabled` value.

For example:
```jsx
<Text disabled={true} accessibilityState={{disabled: false}} />
````
becomes:
````jsx
<Text disabled={true} accessibilityState={{disabled: true}} />
````

## Changelog

<!-- Help reviewers and the release process by writing your own changelog entry. For an example, see:
https://github.com/facebook/react-native/wiki/Changelog
-->

[General] [Fixed] - Text Component doesn't disable click functionality when disabled

## Test Plan

<!-- Demonstrate the code is solid. Example: The exact commands you ran and their output, screenshots / videos if the pull request changes the user interface. -->

[1]. Text has `disabled` and `accessibilityState={{disabled: false}}`
[2]. Text has `disabled`
[3]. Text has `accessibilityState={{disabled: true}}`
[4]. Text has `accessibilityState={{disabled:false}}`
[5]. Text has `disabled={false}`  and `accessibilityState={{disabled:true}}`
7. Test Cases on the main branch
[7.1]. Text has `disabled` and `accessibilityState={{disabled: false}}`
[7.3] Text has `accessibilityState={{disabled: true}}`
[7.5] Text has `disabled={false}`  and `accessibilityState={{disabled:true}}`

[1]: https://user-images.githubusercontent.com/24992535/153145503-220619c3-4008-485d-9295-e0b623a856fc.mp4
[2]: https://user-images.githubusercontent.com/24992535/153145525-80b6a10b-c1b3-44bc-9056-9b8f6cd533f9.mp4
[3]: https://user-images.githubusercontent.com/24992535/153145535-29aeaedc-f7d2-4471-b756-2b5765a7f8ea.mp4
[4]: https://user-images.githubusercontent.com/24992535/153145546-2b945cef-20e5-47cd-b402-4bde941376b2.mp4
[5]: https://user-images.githubusercontent.com/24992535/153145556-9f2d9f33-1adc-4806-8b24-cbb6c4abab75.mp4
[7.1]: https://user-images.githubusercontent.com/24992535/153145560-71dc56d2-f418-467d-98ca-6b51c2c43e69.mp4
[7.3]: https://user-images.githubusercontent.com/24992535/153145570-8c2491ca-74ea-48cd-8a22-87a2655d80ac.mp4
[7.5]: https://user-images.githubusercontent.com/24992535/153145576-25d706e5-31b6-4545-b969-3f20f7c48f8e.mp4
