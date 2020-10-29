# Lab2-3 體驗手動部署應用 (1分)
在此LAB我們將體驗在持續交付階段中的佈署作業，我們將把前面LAB2-1、LAB2-2測試、分析完成，確認可靠的程式發布至OpenShift上。
## 1.登入OpenShift
```
oc login https://c100-e.jp-tok.containers.cloud.ibm.com:32043 --token=${你的Token}
```
## 2.切換到你的工作區
```
oc project ${你的學號}
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-3-1.PNG)
## 2.切換至target目錄查看建置完成的jar檔
```
cd target 
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-3-2.PNG)

## 3.執行以下指令，佈署應用程式(該指令將會自動把你的Java應用程式容器化後部屬至OpenShift)。
```
oc start-build bc/recommendation --from-file recommendation-0.0.1-SNAPSHOT.jar
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-3-3.PNG)
