# Lab2-4 完成 Jenkinsfile (Demo)
在此步驟我們將完成 Jenkinsfile，串起整個 CI/CD 流程，本範例的內容包含 抓取程式碼、單元測試、程式碼品質分析、編譯Java、容器化與佈署，流程如下圖所示。
![Image lab-env](https://raw.githubusercontent.com/j3ffk3/nccu-lab-2020/main/imgs/build-success.PNG)

### 1.於GitHub上打開 recommendation\src\main\resources目錄下既有的 Jenkinsfile
### 2.修改 Stage1 Clone Source Code 下的 url 參數改為你git的位置，範例如下
```
stage('Clone Source Code') {
  steps {
            	echo 'Clone Source Code ...'
		git branch: 'main', url: '${GIT_URL}'
         }
}
```
### 3.查看 Stage2 Unit Test 下的指令，為LAB2-1單元測試下的指令
```
// Stage2 Unit Test
stage('Unit Test') {
	steps {
        	dir("recommendation") {
			sh """
				mvn test
			"""
		}
	}
}
```
### 4.查看 Stage3 Code Quality Analysis ，為LAB2-2 程式碼品質分析下的指令，取代${STUDENT_ID}的部分為你的學號。
```
// Stage3 Code Quality Analysis
stage('Code Quality Analysis') {
	steps {
		dir("recommendation") {
			sh """
				mvn clean package sonar:sonar -Dsonar.projectKey=recommendation-${STUDENT_ID} -Dsonar.projectName=recommendation-${STUDENT_ID}
			"""
		}
	}
}
```
### 5.查看 Stage4Build Jar file ，為LAB2-3 編譯Java 的指令。
```
// Stage4 Build Jar file
stage('Build Jar file') {
	steps {
            	dir("recommendation") {
			sh """
				mvn clean package -DskipTests
			"""
		}
	}
}
```
### 6.查看 Stage5 Build Image & Deploy ，為LAB2-3 佈署應用的指令，取代${STUDENT_ID}的部分為你的學號。

```
// Stage5 Build Image & Deploy
stage('Build Image & Deploy') {
	steps {
            	dir("recommendation/target") {
			sh """
				oc project ${STUDENT_ID}
				oc start-build bc/recommendation --from-file recommendation-0.0.1-SNAPSHOT.jar -F
			"""
		}
	}
}
```
