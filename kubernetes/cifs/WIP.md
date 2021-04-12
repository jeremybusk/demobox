????A
CIFS Flexvolume Plugin for Kubernetes (https://github.com/fstab/cifs). With this Plugin, every user can pass her/his credentials to the Pod. The user only needs to create a Kubernetes secret (cifs-secret), storing the username/password and use this secret for the mount within the Pod. The volume is then mounted as follows:
(...)
  volumes:
  - name: test
    flexVolume:
      driver: "fstab/cifs"
      fsType: "cifs"
      secretRef:
        name: "cifs-secret"
      options:
        networkPath: "//server/share"
        mountOptions: "dir_mode=0755,file_mode=0644,noperm"
