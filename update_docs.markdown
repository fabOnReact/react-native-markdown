update summary

1) change Switch in Text (pr and summary)

```
%s/Switch/Text/g
```

2) remove old links

```
%s/]:.*/]:/g 
```

3) add to stash
```
ga docs/tests/summary.markdown
```

4) update tests

```
rm -f copy/*.markdown
cp original/*.markdown copy
```
open all the 1.markdown till 7.5.markdown in buffer

replace Switch with Text in all buffers
```
bufdo %s/Switch/Text/gce
```

5) record videos
6) upload to github
7) save links
8) generate video tags (use macro)
9) replace video tags
10) update js examples (use macro to copy paste below code)
```javascript
<Text
  style={styles.text}
  onPress={() => console.warn('onPress')}
  disabled
  accessibilityState={{disabled: false}}>
  This is a Text
</Text>
```
