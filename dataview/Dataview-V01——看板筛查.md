

# 看板配置Dataview

## 1、看板-查询最新文件 

```dataviewjs
dv.table(
    [], // column name
    dv.pages()
        // excluded files
        .where(page => page.file.name != "Home" && page.file.name != "Recents"
        && page.file.name != "Tasks")
        // sort by recently updated
        .sort(page => page.file.mtime.toMillis(), "desc")
        .limit(10)
        .map(page => [
            page.file.link + 
            "<span style='color: gray; font-size: 13px; margin-left: 2px; float: right'>" + 
            page.file.mtime.toRelative() + 
            "</span>"
        ])
);
```


## 2、看板-查询任务 

```dataview

TASK
FROM #overview
WHERE !completed
GROUP BY link as origin
SORT origin.file.mtime DESC, text ASC

```















