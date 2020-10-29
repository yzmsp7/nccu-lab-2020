
# Lab2-1 體驗單元測試 (1分)
手動佈署推薦服務，體驗一下程式碼集成、佈署的繁瑣步驟吧!  
1.打開命令提示字元(Windows)或是終端機(Mac)

2.抓取程式碼至你的工作機 
```
git clone https://github.com/${你的GIT帳號}/nccu-lab-2020.git
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-1-1.PNG)

3.切換至recommendation目錄  
```
cd nccu-lab-2020/recommendation/
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-1-2.PNG)

3.執行單元測試
```
mvn test
```
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-1-3.PNG)

4.查看單元測試結果為成功，共8個測試。
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/lab2-1-4.PNG)
