
# Description 

本專題為資料可視化工具的實作，將載入的特定JSON格式資料集以柱狀圖呈現，以下拉式選單決定某特定時間的資料。


## JSON 資料格式

```javascript
{"source":"XX統計處",
 "data":{
     "time1":{"key1":value,
              "key2":value,
              "key3":value},
    "time2":{"key1":value,
             "key2":value,
             "key3":value}
 }}
```

## 使用者介面

![App Screenshot](https://raw.githubusercontent.com/lry121255/s1080308-final-project/main/Layout%20node.png?token=GHSAT0AAAAAACBBP7ST2K4MLMG7XS2SEC7YZBPWFCQ)

![App Screenshot](https://raw.githubusercontent.com/lry121255/s1080308-final-project/main/UI.png?token=GHSAT0AAAAAACBBP7SSOAM4EG73ROSDZRBSZBPWFVQ)




## 按鈕功能

#### file Button
開啟欲呈現資料。
```javascript
Button filebutton = new Button("file");
filebutton.setOnAction((e)->{
    try {
        selectfile(stage);
    } catch (IOException ex) {
        ex.printStackTrace();
    }
});
```
#### selectfile(stage)

使用javafx的filechooser元件選擇json資料檔案，回傳檔案路徑，將此路徑之檔案載入並將時間資料加入下拉式選單。


#### 下拉式選單事件
點選選單內之時間資料繪出該時間點的資料。
```javascript
combobox.setOnAction(event -> {
            String selectedOption = combobox.getValue();
            JSONObject ob = new JSONObject(json_data);
            JSONObject data = ob.getJSONObject("data").getJSONObject(selectedOption);
            pltbar(data);
            System.out.println("option: " + data);
        });
```

#### pltbar(JSONObject data)
輸入時間資料，使用javafx的Barchart繪出資料長條圖。

## Futul work

- 使用者介面優化
- 新增不同資料呈現方式(圓餅圖、折線圖)
- 資料排序功能
- 資料動畫優化
