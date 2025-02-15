apiVersion: v1
kind: PersistentVolume
metadata:
  name: static-content-pv
spec:
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteMany
  hostPath:
    path: "/mnt/data"