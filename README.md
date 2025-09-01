# Anypoint Platform Development: Production-Ready Integrations - DEX670

## Local Path
- PROJECT_HOME=/Users/yehan.jeong/Desktop/dex670-202509
- STUDENT_FILE=/Users/yehan.jeong/Desktop/CDEV-DEX670-EN-25oct2024-Student-Files

## Anypoint Platform Information
- Mule Account: yehan250901

### Business Group
- Business Group ID: 319f9561-cf60-490d-8dab-55ae48d87446
- Client ID: e3e515790d3740fea456727bc035cda1
- Client Secret: C09653C7A7c240328AE8de1Ccba24166

### Connected App
- Exchange Viewer ID: 0d3860f9442b46d3a3e44d5e429c4f3b
- Exchange Viewer Secret: FDD189Cb6A1D42cA9AeDB7ADE4Fbb742
- Exchange Contributor ID: b3d010a7979b488f8287de8e17b23205
- Exchange Contributor Secret: e3e038D23b6C48959a5dcaa2e1CdbeD7

## Commands
- export PROJECT_HOME=/Users/yehan.jeong/Desktop/dex670-202509
- export STUDENT_FILE=/Users/yehan.jeong/Desktop/CDEV-DEX670-EN-25oct2024-Student-Files
- cd $PROJECT_HOME
- mkdir bom
- mkdir parent-pom
- cp $STUDENT_FILE/walkthroughs/devint/module01/wt1-1_starter/bom/pom.xml ./bom/pom.xml
- cp $STUDENT_FILE/walkthroughs/devint/module01/wt1-1_starter/parent-pom/pom.xml ./parent-pom/pom.xml
- cp -r $STUDENT_FILE/walkthroughs/devint/module01/wt1-1_starter/apps-commons ./
- cp -r $STUDENT_FILE/walkthroughs/devint/module01/wt1-1_starter/check-in-papi ./
- mvn install:install-file -Dfile=bom/pom.xml -DpomFile=bom/pom.xml
- mvn install:install-file -Dfile=parent-pom/pom.xml -DpomFile=parent-pom/pom.xml
- cd $PROJECT_HOME/apps-commons
- mvn clean install
- cd $PROJECT_HOME/check-in-papi
- mvn clean verify -U -Dencrypt.key=secure12345 -DskipTests=true
- curl -ik -X PUT -H "Content-Type: application/json" -d "{\"lastName\" :\"Smith\",\"numBags\":2}" https://localhost:8081/api/v1/tickets/PNR123/checkin
- curl -ik -X PUT -H "Content-Type: application/json" -d "{\"payerID\": \"STJ8222K092ST\", \"paymentID\": \"PAY-1AKD7482FAB9STATKO\"}" https://localhost:8081/api/v1/tickets/N123/paymentApproval
- curl -ik https://localhost:8081/alive
- curl -ik https://localhost:8081/ready
- curl -ik -X PUT -H "Content-Type: application/json" -d "{\"lastName\":\"Smith\",\"numBags\":2}" https://localhost:8081/api/v1/tickets/PNR123/checkin


paymentID: "PAY-1AKD7482FAB9STATKO"
paymentID: "PAY-1B56960729604235TKQQIYVY"