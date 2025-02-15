apiVersion: v1
kind: PersistentVolume​Claim
metadata:
  name: static-content-pvc
spec:
  accessModes:
    - ReadWriteMany
  resources:
    requests:
      storage: 1Gi