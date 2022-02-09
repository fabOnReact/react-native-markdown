<!-- Thanks for submitting a pull request! We appreciate you spending the time to work on these changes. Please provide enough information so that others can review your pull request. The three fields below are mandatory. -->

## Summary

<!-- Explain the **motivation** for making this change. What existing problem does the pull request solve? -->

This issue fixes https://github.com/facebook/react-native/issues/30937 ([Test Case 7.1][7.1], [Test Case 7.3][7.3], [Test Case 7.5][7.5]) .
The issue is caused by:

1) the missing prop `accessibilityState` in the Text component https://github.com/fabriziobertoglio1987/react-native/commit/6ab7ab34e56411a7e87f396feb2f7ece1c4f98dd
2) missing setter for prop `accessible` in `ReactTextAnchorViewManager` https://github.com/fabriziobertoglio1987/react-native/commit/17095c6615107695f44af262846da446868b4cd8

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

[1]: https://github.com/fabriziobertoglio1987/react-native-notes/issues/1#issuecomment-1033465424
[2]: https://github.com/fabriziobertoglio1987/react-native-notes/issues/1#issuecomment-1033465631
[3]: https://github.com/fabriziobertoglio1987/react-native-notes/issues/1#issuecomment-1033465706
[4]: https://github.com/fabriziobertoglio1987/react-native-notes/issues/1#issuecomment-1033465755
[5]: https://github.com/fabriziobertoglio1987/react-native-notes/issues/1#issuecomment-1033465813
[7.1]: https://github.com/fabriziobertoglio1987/react-native-notes/issues/1#issuecomment-1033465874
[7.3]: https://github.com/fabriziobertoglio1987/react-native-notes/issues/1#issuecomment-1033465961
[7.5]: https://github.com/fabriziobertoglio1987/react-native-notes/issues/1#issuecomment-1033466018
