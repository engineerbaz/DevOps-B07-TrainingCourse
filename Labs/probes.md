 

kind: Pod
apiVersion: v1
metadata:
    name: liveness-readiness-pod
spec:
    containers:
    - name: server
    image: python:2.7-alpine
# Check that a container is ready to handle requests.
    readinessProbe:
# After five seconds, check for a
# 200 response on localhost:8000/
# and check only once before thinking we've failed.
    initialDelaySeconds: 5
    failureThreshold: 1
        httpGet:
        path: /
        port: 8000
# This container starts a simple web
# server after 45 seconds.
    env:
    - name: DELAY_START
        value: "45"
        command: ["/bin/sh"]
        args: ["-c", "echo 'Sleeping...'; sleep $(DELAY_START);
        echo 'Starting server...'; python -m SimpleHTTPServer"]



---

kind: Pod
apiVersion: v1
metadata:
    name: liveness-readiness-pod
spec:
    containers:
    - name: server
      image: python:2.7-alpine
      readinessProbe:
        initialDelaySeconds: 5
        failureThreshold: 1
        httpGet:
          path: /
          port: 8000
      env:
      - name: DELAY_START
        value: "45"
      command: ["/bin/sh"]
      args: ["-c", "echo 'Sleeping...'; sleep $(DELAY_START); echo 'Starting server...'; python -m SimpleHTTPServer"]