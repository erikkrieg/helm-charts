update +ARGS="":
  #!/usr/bin/env sh
  helm upgrade vpn --create-namespace --install -n headscale --wait {{ARGS}} ./chart 

key:
  kubectl exec deploy/vpn-headscale -n headscale -- headscale users create eksys 
  kubectl exec deploy/vpn-headscale -n headscale -- headscale --user eksys preauthkeys create --reusable --expiration 24h

# ip := "vpn-headscale.headscale.svc.cluster.local"
ip := "192.168.1.14"
port := "30080"
join KEY:
  tailscale up --auth-key={{KEY}} --login-server=http://{{ip}}:{{port}}
