# Lab5_CloudRun_and_ExtraCredit
Lab 5 – gRPC conversion engine, REST API, Cloud Run deployment, and canary rollout
---

# Lab Execution Screenshots

## 1. Environment Setup

![Environment Setup](screenshots/1_environment_setup.png)

This screenshot shows the initial environment setup for the lab. The necessary tools and project files are prepared so the microservices can be developed and deployed.

---

## 2. Clone Repository and Virtual Environment

![Clone Repo](screenshots/2_clone_rep_and_venv.png)

The repository for the lab is cloned and a Python virtual environment is created. This ensures that all dependencies are installed in an isolated environment for the project.

---

## 3. gRPC Install and Restore Script

![gRPC Install](screenshots/3_grpc_install_and_restore_script.png)

This step installs the required gRPC libraries and runs the restore script to configure the project environment. These tools are needed for communication between the API service and the conversion engine.

---

## 4. Restore Script Environment

![Restore Script](screenshots/4_restore_script_environment.png)

The restore script completes the environment setup by installing any additional dependencies needed for the project. This ensures the services can run correctly before building containers.

---

## 5. gRPC Contract and Stub Generation

![gRPC Contract](screenshots/5_grpc_contract_and_stub_generation.png)

The protocol buffer contract is compiled to generate the gRPC client and server stubs. These generated files allow the converter API to communicate with the conversion engine through gRPC.

---

## 6. Conversion Logic and Validation

![Conversion Logic](screenshots/6_conversion_logic_and_validation.png)

This screenshot shows the implementation of the conversion logic and input validation. The system checks that units belong to the same category before performing a conversion.

---

## 7. Container Build and Push

![Container Build](screenshots/7_container_build_and_push.png)

The conversion engine microservice is built into a Docker container and pushed to the container registry. This container image will later be deployed to Google Cloud Run.

---

## 8. Conversion Engine Cloud Run Deployment

![Engine Deploy](screenshots/8_conversion_engine_cloud_run_deploy.png)

The conversion engine container is deployed to Google Cloud Run. This creates the backend service responsible for performing unit conversions.

---

## 9. Converter API Container Build

![API Build](screenshots/9_converter_api_container_build.png)

The converter API service is built as a container image. This service acts as the public interface that users interact with when requesting conversions.

---

## 10. Converter API Cloud Run Deployment

![API Deploy](screenshots/10_converter_api_cloud_run_deploy.png)

The converter API container is deployed to Cloud Run. This step makes the API accessible so it can receive HTTP requests and forward them to the conversion engine.

---

## 11. Service-to-Service IAM

![IAM Setup](screenshots/11_service_to_service_iam.png)

IAM permissions are configured so that the converter API can securely call the conversion engine service. This allows internal communication between the microservices while keeping the conversion engine private.

---

## 12. Successful API Conversion

![Successful Conversion](screenshots/12_successful_api_conversion.png)

A successful conversion request is sent to the API and the correct result is returned. This confirms that the REST API and gRPC conversion engine are communicating correctly.

---

## 13. Multiple Conversions and Error Handling

![Multiple Conversions](screenshots/13_multiple_conversions_and_error_handling.png)

Multiple conversion requests are tested, including an invalid conversion attempt. The system correctly handles valid conversions and returns an error when incompatible units are used.

---

## Cleanup

![Cleanup](screenshots/cleanup_and_delete_services.png)

This screenshot shows the cleanup step where the deployed Cloud Run services are deleted. This ensures that no unnecessary cloud resources remain running after the lab is completed.

---

# Extra Credit – Canary Deployment

The extra credit demonstrates how a new version of a service can be deployed gradually using a canary rollout strategy.

---

## EC 1 – Current Revision and Baseline Test

![Baseline](screenshots/ec_01_current_revision_and_baseline_test.png)

The current revision of the converter API is checked and a baseline conversion test is performed. This confirms that the original version of the service is working correctly before deploying a new version.

---

## EC 2 – Build v2 Container

![Build v2](screenshots/ec_02_build_v2_container.png)

A new container image for version 2 of the converter API is built and pushed to the container registry. This prepares the updated version for deployment.

---

## EC 3 – Deploy v2 With No Traffic

![Deploy v2](screenshots/ec_03_deploy_v2_no_traffic.png)

Version 2 of the API is deployed as a new Cloud Run revision but receives no traffic initially. This allows the new version to be tested without affecting users.

---

## EC 4 – Verify Traffic and Test v2

![Verify v2](screenshots/ec_04_verify_traffic_and_test_v2.png)

The tagged URL for version 2 is used to test the new revision directly. This confirms that the new version works before sending real user traffic to it.

---

## EC 5 – Canary 10% Rollout

![Canary Rollout](screenshots/ec_05_canary_10_percent_rollout.png)

Traffic is split so that 10% of requests go to version 2 while 90% continue using version 1. This gradual rollout helps verify that the new version works correctly under real traffic.

---

## EC 6 – Full Rollout

![Full Rollout](screenshots/ec_06_full_rollout_v2.png)

After confirming the new version is stable, all traffic is routed to version 2. This completes the deployment of the updated service.

---

## EC 7 – v2 Serving Requests

![v2 Serving Requests](screenshots/ec_07_v2_serving_requests.png)

The final test confirms that requests are now being handled by version 2 of the converter API. This verifies that the canary deployment successfully transitioned the service to the new version.
