
# Lab2-2 體驗程式碼品質分析 (1分)
在此LAB我們將體驗在持續集成階段的程式碼品質分析，利用哪些指標來衡量程式碼的好壞，並實際操作。

## 1.查看程式碼品質分析工具SonarQube
```
http://sonarqube-nccu-cicd.nccu-lab-teacher-4c2f3918c1e51a612ffc44c361c1a42f-0000.jp-tok.containers.appdomain.cloud/
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-2-1.PNG)
## 2.執行程式碼品質分析
將${你的學號}替換為你的學後號於終端機或命令提示字元執行 
```
mvn clean package sonar:sonar -Dsonar.projectKey=recommendation-${你的學號} -Dsonar.projectName=recommendation-${你的學號}
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-2-2.PNG)
## 3.查看分析結果
```
http://sonarqube-nccu-cicd.nccu-lab-teacher-4c2f3918c1e51a612ffc44c361c1a42f-0000.jp-tok.containers.appdomain.cloud/
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-2-3.PNG)
