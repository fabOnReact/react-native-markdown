## Summary

This issue fixes https://github.com/facebook/react-native/issues/30977. 
The Pull Request was previously published by [intergalacticspacehighway][13] with https://github.com/facebook/react-native/pull/31666.

The solution consists of:

1. Adding Javascript logic in the [FlatList][14] component to add accessibility information (row and column position) for each FlatList cell. The information is saved on the native side in the AccessibilityNodeInfo and announced by TalkBack when changing row, column, or page ([video example][12]).

2. Adding Java logic in [ReactScrollView.java][16] and HorizontalScrollView to announce pages with TalkBack when scrolling up/down. The missing Android logic in [ReactScrollView.java][10] (see also the [GridView][11] example) is responsible for announcing Page Scrolling with TalkBack.

Relevant discussions https://github.com/fabriziobertoglio1987/react-native-notes/issues/6


## Changelog

[Android] [Added] - Accessibility announcement for list and grid in FlatList

## Test Plan

[1]. TalkBack announces pages and cells with Horizontal Flatlist in the Paper Renderer ([link][1])
[2]. TalkBack announces pages and cells with Vertical Flatlist in the Paper Renderer ([link][2])
[3]. <FlatList numColumns={undefined} /> should not trigger Runtime Error NoSuchKey exception columnCount when enabling TalkBack. ([link][3])

[1]: https://github.com/fabriziobertoglio1987/react-native-notes/issues/6#issuecomment-1050452894
[2]: https://github.com/fabriziobertoglio1987/react-native-notes/issues/6#issuecomment-1050462465
[3]: https://github.com/fabriziobertoglio1987/react-native-notes/issues/6#issuecomment-1032340879

[10]:https://github.com/aosp-mirror/platform_frameworks_base/blob/1ac46f932ef88a8f96d652580d8105e361ffc842/core/java/android/widget/AdapterView.java#L1027-L1029 "GridView.java method responsible for calling setFromIndex and setToIndex"
[11]:https://github.com/fabriziobertoglio1987/react-native-notes/issues/6#issuecomment-1042518901 "test case on Android GridView"
[12]:https://github.com/fabriziobertoglio1987/react-native-notes/issues/6#issuecomment-1050452894 "TalkBack announces pages and cells with Horizontal Flatlist in the Paper Renderer" 
[13]:https://github.com/intergalacticspacehighway "github intergalacticspacehighway"
[14]:https://github.com/fabriziobertoglio1987/react-native/blob/80acf523a4410adac8005d5c9472fb87f78e12ee/Libraries/Lists/FlatList.js#L617-L636 "FlatList accessibilityCollectionItem"
[16]:https://github.com/fabriziobertoglio1987/react-native/blob/5706bd7d3ee35dca48f85322a2bdcaec0bce2c85/ReactAndroid/src/main/java/com/facebook/react/views/scroll/ReactScrollView.java#L183-L184 "logic added to ReactScrollView.java"
