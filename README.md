STEP TO INSTALL COCKROACHDB SECURE CLUSTER:
1. membuat folder certs & ca-key
2. membuat cockroachdb certs menggunakan command:
	> cockroach cert create-ca --certs-dir=certs --ca-key=ca-key/ca.key (untuk cluster)
	> cockroach cert create-client root --certs-dir=certs --ca-key=ca-key/ca.key (untuk root user)
3. Membuat secret:
	> kubectl create secret generic cockroachdb.client.root --from-file=certs
	> kubectl create secret generic cockroachdb.node --from-file=certs
4. deploy cluster
	> kubectl create -f cockroachdb/.
