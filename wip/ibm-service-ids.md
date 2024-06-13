


Service IDs


KP iam-ServiceId-2253d272-d276-4cd6-bec8-9ec60dac264f

iam-ServiceId-ab938c80-036b-4119-b69e-b1b60004d313 - IBM - account used for synchronization
=> owned by the IaaS team, used to sync users in IaaS with users in PaaS

iam-ServiceId-769b5c65-0165-4c89-847d-9660b1632e14 - PULSAR_IAM_SERVICEID - delete member from access group
=> owned by the PaaS Hyperwarp team that delivers asynchronous messaging - deletion of members in access group happens asynchronous

iam-ServiceId-a9e7347c-e7be-4a9e-8dd9-99e1abb72c8f - Resource Controller - create/delete service ID
=> owned by the PaaS Recource Manager team; needed to create service credentials when creating service instances


/var/log/at/*.log /var/log/at/*/*.log /var/log/at/*/*/*.log /var/log/at/*/*/*/*.log /var/log/at/*/*/*/*/*.log /var/log/at/*/*/*/*/*/*.log /var/log/at/*/*/*/*/*/*/*.log /var/log/at/*/*/*/*/*/*/*/*.log /var/log/at/*/*/*/*/*/*/*/*/*.log /var/log/at/*/*/*/*/*/*/*/*/*/*.log
{
    rotate 4
    daily
    missingok
}