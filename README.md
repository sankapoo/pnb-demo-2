demo

Create a temp pod in same namespace
cat <<EOF | oc apply -f -
apiVersion: v1
kind: Pod
metadata:
  name: finance-pvc-debug
spec:
  containers:
  - name: debug
    image: registry.access.redhat.com/ubi8/ubi
    command: ["/bin/bash", "-c", "--"]
    args: ["sleep infinity"]
    volumeMounts:
    - mountPath: /workspace/data
      name: finance-pvc
  volumes:
  - name: finance-pvc
    persistentVolumeClaim:
      claimName: finance-pvc
  restartPolicy: Never
EOF


<img width="1222" alt="image" src="https://github.com/user-attachments/assets/4e3323fe-d091-4cd7-a308-92b88de97926" />
