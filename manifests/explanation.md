### 1. Choice of the Kubernetes Objects used for deployment

- Client and backend, I've used deployment object as they are in static state, there is no state to maintain
- Mongo, I've used StatefulSet object as the database must maintain a state when data is added

### 2. Method used to expose your pods to internet traffic

- Client → LoadBalancer Service (public-facing).
- Backend → ClusterIP Service (internal-only).
- Mongo Database → ClusterIP Service (internal-only).

### 3. Git workflow used to achieve the task.

- Refer README.md