 # SAP BTP

### BTP
*open PaaS (platform as a Service), which provides customers/partners with unique business services for building and extending cloud apps.*

### BTP Cockpit
*web-based UI for administrators, which provides access to a number of functions for configuring and managing apps and connecting them to services on SAP BTP.*

--------------------------------------------------------------------------------------------------------------------

# SAP Cloud Foundry

## 1. What is Cloud Foundry?
Cloud Foundry (CF) is an open-source **Platform-as-a-Service (PaaS)** that allows developers to deploy, run, and scale applications without managing the underlying infrastructure.
- Managed by **Cloud Foundry Foundation**.
- **Multi-cloud**: Runs on AWS, Azure, GCP, OpenStack, etc.
- **Used in SAP BTP**: Provides runtime for applications in SAP Business Technology Platform.

## 2. Key Components of Cloud Foundry
- **Organizations & Spaces**: Logical structures to manage applications.
- **Applications**: Deployed workloads running in CF.
- **Buildpacks**: Predefined environments for apps (e.g., Node.js, Java, Python).
- **Routes**: Map app instances to URLs.
- **Services**: External dependencies (databases, messaging, authentication, etc.).
- **Service Brokers**: Manage service lifecycle (provisioning, binding, unbinding, deprovisioning).

## 3. Cloud Foundry CLI (cf CLI)
Used for managing CF applications and services.

### Common Commands:
```bash
cf login                         # Authenticate to CF
cf target -o <org> -s <space>    # Select organization and space
cf push <app-name>               # Deploy an application
cf apps                          # List deployed applications
cf services                      # List available services
cf bind-service <app> <service>  # Bind service to an app
cf restart <app>                 # Restart application
cf delete <app>                  # Remove an application
cf logs <app> --recent           # View logs
```

## 4. Application Deployment in Cloud Foundry
1. Write the application (Node.js, Java, Python, etc.).
2. Create a `manifest.yml` (optional but recommended):
   ```yaml
   applications:
     - name: my-app
       memory: 256M
       instances: 1
       buildpack: nodejs_buildpack
       env:
         NODE_ENV: production
   ```
3. Push the application using `cf push`.
4. Bind required services (e.g., database, authentication).
5. Scale if needed (`cf scale <app> -i <num_instances>`).

## 5. Cloud Foundry Services in SAP BTP
- **SAP HANA Cloud**: Database as a Service.
- **SAP Application Logging**: Centralized logging.
- **Connectivity Service**: Secure integration with on-premise systems.
- **Authorization & Trust Management (XSUAA)**: Manages authentication & authorization.
- **Job Scheduler**: Schedules background jobs.

## 6. Scaling & High Availability
- **Horizontal Scaling**: Increase/decrease app instances (`cf scale <app> -i <num>`).
- **Vertical Scaling**: Increase allocated memory or disk size (`cf scale <app> -m 512M`).
- **Load Balancing**: CF automatically distributes requests across instances.
- **Self-Healing**: CF restarts failed instances.

## 7. Security in Cloud Foundry
- **Authentication & Authorization**: XSUAA service in SAP BTP.
- **Environment Variables**: Secure configuration without hardcoding.
- **Application Security Groups (ASGs)**: Control network access.
- **Transport Layer Security (TLS)**: Ensures encrypted communication.

**XSUAA Flow:**

![alt text](/imgs/xsuaa_flow.png)

**Role Concept:**

![alt text](/imgs/role_concept.png)

## 8. Multitenancy on Application layer

* *Multitenancy is the ability to serve multiple tenants through single clusters of microservice instances, while strictly isolating the tenants' data. Tenants are clients using SaaS solutions. In contrast to single-tenant mode, _applications wait for tenants to subscribe before serving any end-user requests_.*

* *SaaS applications need to register with the SAP BTP SaaS Provisioning service to handle subscribe and unsubscribe events.*

  1. **Single tenant-like** - one app handle only one customer with one separated DB. Not efficient, time-consuming (should install all the apps independently).

  2. **Multitenant-like** - we still have different DB. 
  
  3. **Full multitenancy** - in DB level here we can use different approaches, and we use here *HDI Containers* concept. For each customer we have separate HDI Container. *Example: we host our **App** on **BTP**, this **App** is connected to **HANA**, where we have different **HDI Containers**, and we understand who is connected by using different **Hosts** (at the beginning of URL).*

![alt text](/imgs/multitenancy.png)

## 9. Logging & Monitoring
- **cf logs <app> --recent**: View logs.
- **Application Logging Service** (SAP BTP): Stores logs centrally.
- **Prometheus & Grafana**: Open-source monitoring tools.

## 10. Cloud Foundry vs. Kubernetes
| Feature               | Cloud Foundry (CF) | Kubernetes (K8s) |
|----------------------|------------------|----------------|
| Deployment Focus | PaaS | Container Orchestration |
| App Deployment | `cf push` (simplified) | Manages containers |
| Scaling | Automatic | Manual or auto-scaling |
| Service Binding | Built-in Service Brokers | Requires custom setup |
| Complexity | Easier for developers | More control but complex |

## 11. Best Practices
- Use **12-Factor App** methodology.
- Store configurations in **Environment Variables**.
- Monitor apps using **Application Logging Service**.
- Bind only necessary services to avoid unnecessary costs.
- Optimize application memory and instance count based on load.
