# Week 2 — Distributed Tracing

During this week, I learned that distributed tracing can be a very useful tool because one can track application requests as they flow from frontend devices to backend services and databases.

## Required Homework

### 1. Instrument our backend flask application to use Open Telemetry (OTEL) with Honeycomb.io as the provider

I was able to instrument the backed flask application to use OTEL with Honeycomb.io as shown in the image below
![image](https://user-images.githubusercontent.com/17044063/225619372-f61e934a-3a14-4cb1-84e9-fe51f9ba0f0c.png)


### 2. Run queries to explore traces within Honeycomb.io
I was also able to run queried to explore traces within Honecomb.io

![image](https://user-images.githubusercontent.com/17044063/225620033-ee78f8b2-5bbf-4e53-aa13-2fda5f0042ba.png)

### 3. Instrument AWS X-Ray into backend flask application
### 4. Configure and provision X-Ray daemon within docker-compose and send data back to X-Ray API
### 5. Observe X-Ray traces within the AWS Console
### 6. Integrate Rollbar for Error Logging
### 7. Trigger an error an observe an error with Rollbar
### . Install WatchTower and write a custom logger to send application log data to CloudWatch Log group
