
**-> [Back to Index](./README.md)**


Debug writing in container:
```
oc exec -it simple-api-deployment-57bffb5cc-dqqpf -- sh
id
echo "test" > /app/src/data/test.txt
cat /app/src/data/test.txt
ls -lah /app /app/src /app/src/data
```