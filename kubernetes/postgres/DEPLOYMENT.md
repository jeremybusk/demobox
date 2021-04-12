Some considerations with deployment

Instead of using config maps you can use something like
```
    spec:
      containers:
      - image: postgres:12
        name: postgres
        env:
          - name: POSTGRES_PASSWORD
            value: password 
          - name: POSTGRES_DB
            value: awesomedb
          - name: POSTGRES_USER
            value: amazinguser
          - name: POSTGRES_PASSWORD
            value: perfectpassword
```
