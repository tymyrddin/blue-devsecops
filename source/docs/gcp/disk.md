# Persistent Disk

Google Persistent Disk is a part of the GCP block storage.

To encrypt a persistent disk, in a specific GCP project, in a specific region, using a specific encryption key:

```text
gcloud compute disks \
    create encrypted-disk \
    --kms-key \ projects/[KMS_PROJECT_ID]/locations/[REGION]/
    keyRings/[KEY_RING]/cryptoKeys/[KEY]
```

## Best practices

* Encrypt both the OS and data volumes.
* Encrypt each data volume at creation time.
* Encrypt the machine instance snapshots.
* For highly sensitive environments, encrypt persistent disks using a CMK inside Google Cloud KMS.
* Set names for Google's persistent disks to allow you to have a better understanding of which persistent disk belongs to which machine instance.
* Use tagging (labelling) for persistent disks or snapshots for a better understanding of which disk or snapshot belongs to which machine instance.

