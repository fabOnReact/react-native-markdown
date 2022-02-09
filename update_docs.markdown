update summary

1) change Switch in Text
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
