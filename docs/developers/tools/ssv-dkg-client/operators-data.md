---
sidebar_label: 'Operators Data'
sidebar_position: 1
---

# Operators Data

In order to run any operation with the `ssv-dkg` tool, it is necessary to provide the ID, the public key, and the IP of the operator set that should take part in the DKG ceremony  (which are not provided by the `ssv-dkg` tool itself.)
First of all, select your preferred group of operators from the operator registry of the SSV network. The required Operators data can be collected via the [SSV API](https://api.ssv.network/documentation/#/v4) and [SSV Explorer](https://explorer.ssv.network/).
Operators data can then be supplied to the `ssv-dkg` tool as an argument or through a `json` file, as shown in the example below:


```json
[
  {
    "id": 143,
    "public_key": "LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JSUJJakFOQmdrcWhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBM2VyQk9IUTVJYkJmL3lxak1UMmYKNElQYWJBMkY4YmwzQWlJVStRQlBUd2s2UFRRZS9EZVZMVkx6cm5wWFdZemNTRUZVSnZZeU5WM3ZhYkxGN2VDZwpxNlptRUJhSHN5S2NYS0g5N0JCb21VaDF4TGl5OFRGTkk0VGdjL0JwSU51dEdrRGkrVUhCT0tBcHE0TUVaSXlsCnJpTHlaeDFNZnJ6QTF0ZUNRaVJ3T2tzN0wrT1IraElNOEwvNFRtTUd4RDFhS2tXOHhpUzlKL256YXB5YkxsczMKR3cwWER0Q25XLzREWFVLSm1wLzFrMHlNeHZjT1phUjJWSjB0aUFVMjBKNDcrcUtndi9kZHI1YjNjQ2F5NDhpVQptcks2MkNEaHdyNVpqaU1WSHg2R1NJK0kvZmhMckI2Z2dSdTBYVVVFYTljNzVvR3k1SHVKSFA5dTJIQ0dZSXI5CjBRSURBUUFCCi0tLS0tRU5EIFJTQSBQVUJMSUMgS0VZLS0tLS0K",
    "ip": "https://141.94.143.182:3030"
  },
  {
    "id": 219,
    "public_key": "LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JSUJJakFOQmdrcWhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBcjNlTjVhR205NTN5U0VrcHBDZnAKZmp2bFpMaG51Y0c2ajI2emxHYjNobHcvVXE5aG9tSmhzOVUzTHFuYzU4dk5RR2pENzhCTUZOMy8xUStXanZRSgpuQVJJVVdJTnJONWNoMFBTMXBqb21CVlB0Nkg0RE5ha1lSamxCM0V0QmZGaGFOcDdlQzd4dGFMbzc3Qk5velMxCjBBOFpSRC9IaGg3T3lkNWttUWVnV1pIOGlGRCszcHZnV1ZMUWFibkZuK00xWW9LYUhDNkRHSzdnSzdEYTRlMGcKUTF4MFRhSmRZMUUvcStUQ01oUGhwcmtoVlFlNFBLU0NKOWJHSnRDblBpRUFqa2VWa09RZlA0Z095b0VjaW5jMQpTR2pveVo1dVZPU1hEZGYzVzdYUE9pZEpFU1VoY1hqS05DMC9IN09ZM2pqdTZyUU9NZmFqSERhb3VSWEJGaHZDCnp3SURBUUFCCi0tLS0tRU5EIFJTQSBQVUJMSUMgS0VZLS0tLS0K",
    "ip": "https://209.35.77.243:12015"
  },
  {
    "id": 33,
    "public_key": "LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JSUJJakFOQmdrcWhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBdmo5UmpQTFk5YXd1WVc3NVRVcVoKVWozRWRMN2NkdDFnUjlydHowQU02TENNbTdCNG5DcW1RYjRCeFBsUktVeVl1ZnNEbXIzeTVqUmdVbHBHR0ZRawpOWmU0VGRZQkxPNnRUZ1NyMXphMUlGR0R2dzdJUUJZSHoramFEYVN6Zk9vYnNiUldiMDVaZFdGc01keGlEam5vCnR2NHZ4eGpCOWlXa2xmaytUNXB4K3ZwTWZnd1M2Ui9EOU84Y0dZdTg1b0RpQXgzQ0tPampuY3BPV0pndHhxZUMKbENDbldxSS9PeTFSa1FVcFNYL1hsRHozSHhCN0NlY0IzeUUwNnNTbXd1WTZHdk9tMUEvMmdNVUprbDFTUmFjbgpDeFhYK1hVWWFEemZGdXBBeWxPVnIxMEFnUkpTcVd2SkoxcnJCZkFwSzBMNzFMQzFzVzRyWjloMGFIN2pweW1aCjF3SURBUUFCCi0tLS0tRU5EIFJTQSBQVUJMSUMgS0VZLS0tLS0K",
    "ip": "https://51.81.109.67:3030"
  },
  {
    "id": 190,
    "public_key": "LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JSUJJakFOQmdrcWhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBeEowZDYxN09BSHpxOUQzTUt2WFoKTEJRR2VzVU4xZGFXOC9MNEt4UWJFVlN6Y2JzTlY1Q1RqNm5OWGtnOW1LQzIyWWRRazRZcGpNbk9reENrMXNXRApvUXI4bG4zZTJxbU9zeHJuOGFxZEJhVGZmaFZ4WDJrTU9BZUZCcEJPN0lrTXBOUTFwMzdDMzh0Rmx0eFpxSEt3CkFJVXg5UjVGWWhOZXhrOEUrQlpMYzJFSzl4bjZIMTFUY21hN2NVZW03VUpDeUR3VFlLVC9JN21ZTXV3UGFpTTAKTm1Ta0JoeFYrdkd3bmJqWWhCaEZQTi9MMTJRWi9YZUVJcHFzcGRKTFpkUmhRd2VlZG1MdTNLcXdFdnhhNEJZVQpWcTlkeG9qd1JDdU9TL2tvM1pTQ3hubWpJaHlGQUJXYW5WU2x5TW5xdGFaZTFkdm1STG12RTFpL3RjN251MnRnCi93SURBUUFCCi0tLS0tRU5EIFJTQSBQVUJMSUMgS0VZLS0tLS0K",
    "ip": "https://80.181.85.114:3030"
  },
  {
    "id": 34,
    "public_key": "LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JSUJJakFOQmdrcWhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBNHZMUm93Ry9HeVFYdnFaS092MzEKYlNkRVFId3FoTmR2d2JCckdyYlQ0dmVWVHNPbDNPRVF6K3dWMjBVaXJjeHBVVVRKc081K0wrTzlnR0xNMWdTRgpFMVJRU01zMXEzSkZtNlY0VXFQU3pMK09DcDlMS3ZIRnJKMmU4VGwyZ25UU0tPNzFncGtUdFRrb2ZlLzlJRjFOCmNZMDlJbkQwTWNtZzk1Qm14alBuREV3VE1uVzBQU3JVTnJQYVNlMTJTVHJ0Q2JCTUJFUFR5RnI5elovRWFESFIKSHFaZjlkeE9VMjBiQnNSUVlSMnhCZFBtWHFKaFZZMTQrOExmaWpLRmhMcDNmZ25IL0xtK0NjTE5FOFQ3ZjhTTApoZUhLcnMrcUV4VERTcDR4MWhLMzk4dnpWTElOL0h6T20yeXV3Z3cxeG9zdThTOFlVUzNCeTFGZ3g2RExZc3RyCmxRSURBUUFCCi0tLS0tRU5EIFJTQSBQVUJMSUMgS0VZLS0tLS0K",
    "ip": "https://148.113.20.206:3030"
  }
]
```