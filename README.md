
Question 1
Scenario: Deploying a Multi-Container Application with Docker Compose and Kubernetes You are tasked with deploying a multi-container application that includes a web server (Nginx) and a database (MySQL).
Initially, you need to set it up using Docker Compose and later migrate it
to Kubernetes.

Approach:
Use nginx:latest image
Create a service type NodePort

Solution: 
docker-compose.yaml , nginx-deployment.yaml , nginx-service.yaml , mysql-deployment.yaml , mysql-service.yaml

Question 2

Scenario: Configuring Persistent Storage in Kubernetes for a Stateful Application. You need to deploy a MySQL database on Kubernetes with persistent storage so that the data is not lost even if the pod restarts.
How would you configure persistent storage for the MySQL database?

Approach:
Create a Persistent Volume (PV) of storage 1Gi &
accessModes of ReadWriteOnce
Create a Deployment for the MySQL Database with PVC
with image mysql:5.7

Solution:
mysql-deployment.yaml , mysql-service.yaml , mysql-pv.yaml , mysql-pvc.yaml

Question 3

Scenario : Auto-Scaling a Kubernetes Deployment. Based on CPU Utilisation You have a web application running on Kubernetes and want to ensure that the application scales automatically based on CPU utilisation.
How would you configure Horizontal Pod Autoscaling (HPA) for this
application?

Approach:
Use nginx:latest to create your web application
Deploy the Application
With requests of 100m cpu & limits of 500m cpu
Create Horizontal Pod Autoscaler with
minReplicas = 1
maxReplicas = 10
targetCPUUtilizationPercentage = 50

Solution:
nginx-deployment.yaml , nginx-hpa.yaml

Question 4
Scenario : Create a ConfigMap and Use it in a Deployment
Create a ConfigMap containing a custom HTML page content and update the Nginx deployment to use this ConfigMap to serve the custom page.
custom-page.html
<!-- custom-page.html -->
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LW Nginx Page</title>
</head>
<body>
<h1>Hello from LW Nginx Page!</h1>
<p>This is a LW custom page served by Nginx using Kubernetes ConfigMap.</p>
</body>
</html>

Approach:
Create the Config map
Update the Nginx Deployment
USe the image nginx:latest

Solution:

Question 5

Scenario : Creating and Using a Service Account for Access Control Create a Service Account with specific roles and permissions, and use this Service Account in a Deployment to access a Kubernetes
Secret.

Approach:
Service account name is my-service-account
Create Role with permissions
apiGroups: [""]
resources: ["secrets"]
verbs: ["get", "list"]
Create a RoleBinding to Bind the Role to the Service
Account
Create a secret with hey my-key & value Redhat
Deploy an Application Using the Service Account
Use image busybox with the commands
["sh", "-c", "cat /etc/secrets/my-key"]

Solution:
