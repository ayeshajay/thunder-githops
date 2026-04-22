## Thunder GitOps guide with thunder

1. Setup OpenChoreo cluster and create thunder-idp namespace - https://openchoreo.dev/docs/getting-started/quick-start-guide/
2. Install Thunder component type - https://github.com/asgardeo/thunder/pkgs/container/helm-charts%2Fthunder-oc-componenttype 
3. Install flux in the OC cluster - `kubectl apply -f https://github.com/fluxcd/flux2/releases/latest/download/install.yaml`
4. Clone https://github.com/ayeshajay/thunder-githops git repo and run `kubectl apply -f flux/`

## New change onboard mechanism

1. Update the workload file with the new change - https://github.com/ayeshajay/thunder-githops/blob/main/namespaces/thunder-idp/components/thunder/workload.yaml
2. Merge automated PR in https://github.com/ayeshajay/thunder-githops/pulls and it will be automatically deployed to dev environment
3. Trigger https://github.com/ayeshajay/thunder-githops/actions/workflows/promote.yaml to promote changes to higher environments

## Thunder access

Add hostname mapping for following domains with 127.0.0.1 
  - development-thunder-thunder-idp.openchoreoapis.localhost
  - staging-thunder-thunder-idp.openchoreoapis.localhost
  - Production-thunder-thunder-idp.openchoreoapis.localhost

Can access console using following urls
  - http://development-thunder-thunder-idp.openchoreoapis.localhost:19080/console/
  - http://staging-thunder-thunder-idp.openchoreoapis.localhost:19080/console/
  - http://production-thunder-thunder-idp.openchoreoapis.localhost:19080/console/ 
