
# LAB1 手動佈署推薦服務 (3分)
手動佈署推薦服務，體驗一下程式碼集成、佈署的繁瑣步驟吧!  
1.先至以下網頁右上角輸入你的學號，可以看到目前有的信用卡產品，但下方還沒有推薦結果顯示，推薦結果要在你部署完成後才會顯示。
```
http://credit-card-web-nccu-lab2-common.nccu-lab-teacher-4c2f3918c1e51a612ffc44c361c1a42f-0000.jp-tok.containers.appdomain.cloud/
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab1-before.PNG)

2.抓取程式碼至你的工作機 ，並切換至 recommendation 目錄  
```
cd recommendation
```
3.單元測試
```
mvn test
```
4.程式碼品質掃描
```
mvn clean package sonar:sonar -Dsonar.projectKey=recommendation-${你的學號} -Dsonar.projectName=recommendation-${你的學號}
```
5.查看程式碼品質掃描結果
```
http://sonarqube-nccu-cicd.nccu-lab-teacher-4c2f3918c1e51a612ffc44c361c1a42f-0000.jp-tok.containers.appdomain.cloud/
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab1-scan.PNG)

6.編譯Java程式
```
mvn clean package -DskipTests
```

7.佈署應用程式
- 登入OpenShift
```
oc login https://c100-e.jp-tok.containers.cloud.ibm.com:32043 --token=${你的Token}
```
- 逐行執行以下指令，佈署應用程式
```
oc start-build bc/recommendation --from-file ./target/recommendation-0.0.1-SNAPSHOT.jar
```

8.至以下網頁右上角輸入你的學號，查看推薦內容是否出現，若出現則表示LAB1 已完成
```
http://credit-card-web-nccu-lab2-common.nccu-lab-teacher-4c2f3918c1e51a612ffc44c361c1a42f-0000.jp-tok.containers.appdomain.cloud/
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab1-after.PNG)
