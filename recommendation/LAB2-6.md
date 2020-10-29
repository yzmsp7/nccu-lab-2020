# Lab2-6 設定 WebHook (1分)
在此步驟我們將為LAB2-5完成的 Pipeline 設定WebHook，整合Webhook後在程式碼異動後將自動觸發流程，進一步加速團隊的開發協作速度。

Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/build-success.PNG)

### 1.測試 Pipeline API
OpenShift 提供了啟動 Pipeline 的 API，填上你的學號與密碼後，在 Postman 上嘗試利用POST Method 呼叫，你會發現Pipeline被啟動了
```
https://c100-e.jp-tok.containers.cloud.ibm.com:32043/apis/build.openshift.io/v1/namespaces/${你的學號}/buildconfigs/recommendation-pipeline/webhooks/${密碼}/generic
```
### 2.確認流程是否啟動 
至 OpenShift UI 上查看流程是否正常啟動。
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/build-success.PNG)

### 3.設定WebHook
將此 API 的 URL 設定至GitHub，GitHub 會於程式碼有異動時自動呼叫Pipeline的API啟動CI/CD流程。
至github 點選設定 > webhook 貼上步驟1得到的url，即完成設定。
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-webhook2.PNG)

### 4.驗證
- 嘗試在GitHub上直接編輯，把RecommendationCtl.java 內的 getRecommandateCreditCard() method 的回傳筆數由3改成5，看看CI/CD Pipeline 流程是否正常啟動
- 完成後發現 Web UI 上推薦的筆數變為5筆了，Web連結如下。
```
http://credit-card-web-nccu-lab2-common.nccu-lab-teacher-4c2f3918c1e51a612ffc44c361c1a42f-0000.jp-tok.containers.appdomain.cloud/
```
