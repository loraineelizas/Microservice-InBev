**Technical Challenge: Build a Scalable Microservice with CI/CD, Kubernetes manifest files, and Unit Testing**

***Objective***

Implement a microservice that receives requests via API, validates the input, and writes the data to a database. The project should include CI/CD using GitHub Actions, a Containerfile for containerization, unit test coverage, comprehensive project documentation, and Kubernetes manifest files for deployment in a Kubernetes environment.

Regarding performance, it is essential to provide the architecture and documentation detailing how the service can be scaled efficiently, ensuring it can handle read and write operations within 500ms. The solution should be architected to maintain this performance even as the volume of data scales to millions or billions of records. While the actual implementation of this scalability is not required, the documentation should clearly explain the proposed approach to ensure performance and scalability.

Keep in mind, if everything is complex enough to make much time, it does not need to be implemented at all. But, the documentation should make clear which are the <TODOs>, the estimation time of their development and why they are important for the project.

***Requirements***

1.                  **Microservice Development:**

o        **Language:** TypeScript (Node.js) or Python (Flask/FastAPI).

o        **Functionality:**

§     **POST /data:** Accepts JSON data and stores it.

§     **GET /data:** Retrieves the stored data.

o        **Performance:** Ensure that read/write operations are within 500ms and do not degrade by more than 10% over time, even with a large data volume.

2.                  **Performance Architecture:**

o        **Scalability:** Describe the architectural decisions to ensure the service can handle high volumes of data efficiently.

·                **Data Storage:** Choose an appropriate database (e.g., Redis, MongoDB, PostgreSQL) and justify the choice.

·                **Containerization:**

o        **Containerfile:** Create a Dockerfile to containerize the application.

o        **Docker Compose:** (Optional) Use Docker Compose for multi-container setups if necessary.

3.                  **Kubernetes Deployment:**

·                **Manifest Files:** Create Kubernetes manifest files to have the service deployed in a K8s environment.

·                **CI/CD Pipeline:**

o        **GitHub Actions:** Set up a CI/CD pipeline using GitHub Actions to:

§     What do you suggest?

4.                  **Unit Testing:**

o        **Tests:** Write unit tests for the core functionality of the application.

o        **Coverage:** Ensure a reasonable test coverage

5.                  **Documentation:**

o        **README File:** Include a README.md file with:

§     Project overview and description.

§     Setup instructions for local development.

§     Step-by-step instructions for building, testing, and deploying the application.

§     Explanation of the CI/CD pipeline.

§     Architecture overview and rationales behind technology choices and design decisions.

***Deliverables***

6.                  **Source Code:** Complete source code of the microservice.

7.                  **Dockerfile and Kubernetes Manifests:** Properly configured Dockerfile and Kubernetes manifest files.

8.                  **GitHub Actions Workflow:** Configuration files for the CI/CD pipeline.

9.                  **Unit Tests:** Unit tests with clear instructions on how to run them.

10.             **README File:** A comprehensive README.md file as described above.

***Evaluation Criteria***

11.             **Functionality:** The microservice should work as expected, processing and retrieving data correctly.

12.             **Performance:** The service should maintain read/write operations within 500ms, with architectural plans to scale efficiently (if implemented). Otherwise, the architecture will be evaluated.

13.             **Code Quality:** Code should be clean, well-organized, and follow best practices.

14.             **Testing:** Presence and quality of unit tests and their coverage.

15.             **CI/CD Pipeline:** Correct setup and functionality of the CI/CD pipeline.

16.             **Containerization and Deployment:** Proper Dockerization and successful deployment to Kubernetes.

17.             **Documentation:** Clarity and completeness of the README file.

***Submission***

·                **GitHub Repository:** Provide a link to a public GitHub repository containing the project.

·                **Instructions:** Ensure all instructions are clear and concise for setting up, testing, and deploying the application.



# Pre-requisites

You must have Docker installed for this code to work! Check the [Installation Guide](https://docs.docker.com/engine/installation/) if you haven't got it installed.

# Coding

To start or stop the test database, build the test-database image and run it:

```bash
cd ./test-database
docker build -t test-database .
docker run -it -p 3306:3306 test-database
```

Some commands for working with the test server:

```bash
cd ./users-service
npm install         # setup everything
npm test 			# unit test - no need for a test database running
npm start           # run the server - you must have a test database running
npm run debug       # run the server in debug mode, opens a browser with the inspector
npm run lint        # check to see if the code is beautiful
```

You can also run the test server in its own container:

```bash
docker build -t users-service .
docker run -it -p 8123:8123 --link db:db -e DATABASE_HOST=DB users-service
```

# Integration Testing

To test the entire stack, run:

```bash
docker-compose build
docker-compose up -d
sleep 10 # give the database server enough time to start!
cd integration-test && npm install && npm start && cd ..
docker-compose down
```
