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
- curl -i -X POST -H "Accept: application/json" -H "Accept-Language:en_US" -u "APP-80ANYAIRLINE8184JT3:1929FHDUAL8392K9ABKSNMM" -d "grant_type=client_credentials" https://training-paypal-fake-api-sandbox-mjf1rw.5sc6y6-1.usa-e2.cloudhub.io/v1/oauth2/token
- curl -i -X POST -H "Content-Type: application/json" -H "Authorization: Bearer 8s9kaj3.SDkkd4145_ZsrqVh38sjdhNsqrEU9xem4QJ6sQa36VHfyuBes" -d "{ \"intent\":\"sale\", \"payer\": {\"payment_method\":\"paypal\" }, \"transactions\":[ { \"amount\":{\"total\":\"80.00\", \"currency\":\"USD\" }, \"description\": \"Check-In Baggage.\", \"custom\": \"ANYAIRLINE_90048630024435\",\"invoice_number\": \"48787589673\", \"payment_options\":{\"allowed_payment_method\":\"INSTANT_FUNDING_SOURCE\" },\"soft_descriptor\":\"ANYAIRLINE BAGGAGE\" } ], \"note_to_payer\":\"Behappy.\" }" https://training-paypal-fake-api-sandbox-mjf1rw.5sc6y6-1.usa-e2.cloudhub.io/v1/payments/payment
- curl -i -X POST -H "Content-Type: application/json" -H "Authorization: Bearer 8s9kaj3.SDkkd4145_ZsrqVh38sjdhNsqrEU9xem4QJ6sQa36VHfyuBes" -d '{\"intent\":\"sale\", \"payer\": {\"payment_method\":\"paypal\"}, \"transactions\":[{\"amount\":{\"total\":\"80.00\", \"currency\":\"USD\"}, \"description\": \"Check-In Baggage.\", \"custom\": \"ANYAIRLINE_90048630024435\",\"invoice_number\": \"48787589673\", \"payment_options\":{\"allowed_payment_method\":\"INSTANT_FUNDING_SOURCE\"},\"soft_descriptor\":\"ANYAIRLINE BAGGAGE\"}], \"note_to_payer\":\"Behappy.\"}' https://training-paypal-fake-api-sandbox-mjf1rw.5sc6y6-1.usa-e2.cloudhub.io/v1/payments/payment
- curl -ik -H "Content-Type:text/xml" -d "<CancellationNotification><PNR>KFC1234567890</PNR><PassengerLastName>Jeong</PassengerLastName></CancellationNotification>" https://localhost:8081/api/cancelFlight
- curl -ik -H "Content-Type:text/xml" -d "<CancellationNotification><PNR>KFC123</PNR><PassengerLastName>Jeong</PassengerLastName></CancellationNotification>" https://localhost:8081/api/cancelFlight
- curl -ik -H "Content-Type:text/plain" -d "invalid content type" https://localhost:8081/api/cancelFlight
- curl -ik -H "Content-Type:text/xml" -d "" https://localhost:8081/api/cancelFlight
- curl -ik -H "Content-Type:text/xml" -d "invalid content type" https://localhost:8081/api/cancelFlight
- curl -ik -H "Content-Type:text/xml" -d "<CancellationNotification><PNR1>PNR123</PNR1><PassengerLastName2>Mule</PassengerLastName2></CancellationNotification>" https://localhost:8081/api/cancelFlight
- curl -ik -H "Content-Type:text/xml" -H "X-CORRELATION-ID: KFC12345" -d "<CancellationNotification><PNR>PNR123</PNR><PassengerLastName>Mule</PassengerLastName></CancellationNotification>" https://localhost:8081/api/cancelFlight

