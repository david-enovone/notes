
`git log --author="David Schreck" --pretty=format:"%ad" --date=short main | sort | uniq -c`


```
      3 2024-09-02
      5 2024-09-13
      1 2024-09-18
      1 2024-09-19
      2 2024-09-30
      9 2024-10-01
      5 2024-10-02
      8 2024-10-03
      7 2024-10-04
      5 2024-10-05
      1 2024-10-06
```

`git log --author="David Schreck" --since="2024-10-02" --until="2024-10-09" --pretty=oneline | wc -l`

