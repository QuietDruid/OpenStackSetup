apiVersion: apps/v1
kind: Deployment
metadata:
  name: static-site
spec:
  replicas: 2
  selector:
    matchLabels:
      app: static-site
  template:
    metadata:
      labels:
        app: static-site
    spec:
      containers:
      - name: nginx
        image: nginx:alpine
        ports:
        - containerPort: 80
        volumeMounts:
        - name: static-content
          mountPath: /usr/share/nginx/html
      volumes:
      - name: static-content
        persistentVolumeClaim:
          claimName: static-content-pvc
---
apiVersion: v1
kind: Service
metadata:
  name: static-site
spec:
  ports:
  - port: 80
    targetPort: 80
  selector:
    app: static-site