
kubectl create cronjob currentob --image=busybox --schedule="*/1 * * * *" -- echo "Current date: $(date)"
