# Lab2-3 體驗手動部署應用 (2分)
在此LAB我們將體驗在持續交付階段中的佈署作業，我們將把前面LAB2-1、LAB2-2測試、分析完成，確認可靠的程式發布至OpenShift上。
### 1.查看信用卡網頁
先至以下網頁右上角輸入你的學號，可以看到目前有的信用卡產品，但下方還沒有推薦結果顯示，推薦結果要在你部署完成後才會顯示。
```
http://credit-card-web-nccu-lab2-common.nccu-lab-teacher-4c2f3918c1e51a612ffc44c361c1a42f-0000.jp-tok.containers.appdomain.cloud/
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab1-before.PNG)

### 2.登入OpenShift
```
oc login https://c100-e.jp-tok.containers.cloud.ibm.com:32043 --token=${你的Token}
```
### 3.切換到你的工作區
```
oc project ${你的學號}
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-3-1.PNG)
### 4.切換至target目錄查看建置完成的jar檔
```
cd target 
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-3-2a.PNG)

### 5.執行以下指令，佈署應用程式(該指令將會自動把你的Java應用程式容器化後部屬至OpenShift)。
```
oc start-build bc/recommendation --from-file recommendation-0.0.1-SNAPSHOT.jar
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-3-3.PNG)

### 6.驗證
至以下信用卡網頁右上角輸入你的學號，查看推薦內容是否出現，若有出現則表示佈署成功
```
http://credit-card-web-nccu-lab2-common.nccu-lab-teacher-4c2f3918c1e51a612ffc44c361c1a42f-0000.jp-tok.containers.appdomain.cloud/
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab1-after.PNG)
