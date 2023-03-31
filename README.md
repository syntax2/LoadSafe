# LoadSafe
LoadSafe is a platform that performs rigorous load testing to ensure your website is production-ready. It uses **k6** to simulate user traffic and test website performance under heavy loads. LoadSafe integrates with **Prometheus** and **Grafana** to provide real-time insights and beautiful visualizations of performance metrics.

**To run the project, you can follow these steps:**

1. Clone the project repository from GitHub.
2. Install Docker and Docker Compose if they are not already installed on your system.
3. Navigate to the root directory of the project in your terminal.
4. Run the following command to start the Prometheus and Grafana containers:   
             `docker-compose up -d prometheus grafana`

- This command will start the Prometheus and Grafana containers in detached mode, allowing you to run other commands in the same terminal.

- Prometheus will be available at http://localhost:9090.

- Grafana will be available at http://localhost:3000.

**Run the following command to start the load testing :** 

`K6_PROMETHEUS_RW_TREND_AS_NATIVE_HISTOGRAM=true \
  k6 run -o experimental-prometheus-rw --tag testid= ./samples/test.js`

- This command will run the load testing script using K6, and will output the results in Prometheus format.
- The testid --tag is optional but recommended, as it will allow you to identify the specific test run in the Grafana dashboard, for     (e.g in above command **--tag testid=first_load**)

*After the load testing is complete, you can view the results in the Grafana dashboard by visiting http://localhost:3000.*
*Log in to Grafana using the default credentials (username admin, password admin).*


*The benefit of load testing your website before deploying it to production is that it allows you to identify and fix performance issues before they affect your users. By simulating a large number of concurrent users, you can determine the maximum capacity of your website and ensure that it can handle the expected traffic. Using K6 for load testing and Prometheus and Grafana for visualization allows you to easily generate and analyze performance metrics, and make informed decisions about scaling and optimization.*

