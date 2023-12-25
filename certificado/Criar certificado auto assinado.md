# Criar certificado auto assinado

$ openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout cert.key -out cert.crt -subj "/CN=world.universe.mine/O=world.universe.mine"
Generating a RSA private key
.................................................+++++
................................................................................+++++
writing new private key to 'cert.key'
-----
controlplane $ ls
cert.crt  cert.key  filesystem
controlplane $ cat cert.crt 
-----BEGIN CERTIFICATE-----
MIIDWTCCAkGgAwIBAgIUSVUa5147QebxCtcwotcIMXJSQUMwDQYJKoZIhvcNAQEL
BQAwPDEcMBoGA1UEAwwTd29ybGQudW5pdmVyc2UubWluZTEcMBoGA1UECgwTd29y
bGQudW5pdmVyc2UubWluZTAeFw0yMzEyMjIyMjI2MDZaFw0yNDEyMjEyMjI2MDZa
MDwxHDAaBgNVBAMME3dvcmxkLnVuaXZlcnNlLm1pbmUxHDAaBgNVBAoME3dvcmxk
LnVuaXZlcnNlLm1pbmUwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDi
vTthg3HaoFfp12Opuj9k4swq72JkbyIeJUIanca/0x2DI2WwzoAd578Fg6wI2ag9
jSHEezKLuuluPOZH0zYhXnF8VntLB8w5sxRx6mSUbW/TkaxZVLj0aoYPhNSxba56
Afn9ZAwUmCYHqnq6ssCpTKXblZrtxw8jL42hqR/a06mE0M7iKofWhF2tIdmbcBRu
6ixH1RWJ/t+ASiA0LmfMssDI6f9hFulqWWHxaNSkOjT+QHlGWVoxzCImromvQSpA
MbJmsp9JG8H9qd/Nlfp0kiWwKOM0KkwM53uA0UEGFmsDIwWQkWvVmbRS/T2jRT+J
Sy5gd4h7SygzblOFFoAPAgMBAAGjUzBRMB0GA1UdDgQWBBQ9e1EUC/cAPa56Pw8h
3tFDWtWbBzAfBgNVHSMEGDAWgBQ9e1EUC/cAPa56Pw8h3tFDWtWbBzAPBgNVHRMB
Af8EBTADAQH/MA0GCSqGSIb3DQEBCwUAA4IBAQA9rgtjWT1CUzrY7Qz57879NU5S
P6nAISChGnkSP/becfVde7w0su3X0glTXVturQQdsmRW6TFSMnYOeiUg5lsyPz9Q
WEYs2XWyaQpuv1vIaaQu8qEXZYeS+G2MOmbEKrJNIuM4VbWusSyvKP0vIaJg2nOK
aC8peLNVybMs89VmJTRIKgdpwCGPLDVECXoCt05EzdlLfO6LOBhumlxY4ZyEgdi4
S90VdoP58I2NRkhBoNur3f1Os8fOCbN7Tg5dDPaaMPVesVaQgwC8KUwTCemMNffd
0b512C6aVbSZJ3mTo8KE4KCagukjraPWCXWZKT2TjyrMK/vAcdcpehn1jHJh
-----END CERTIFICATE-----
controlplane $ cat cert.key 
-----BEGIN PRIVATE KEY-----
MIIEvwIBADANBgkqhkiG9w0BAQEFAASCBKkwggSlAgEAAoIBAQDivTthg3HaoFfp
12Opuj9k4swq72JkbyIeJUIanca/0x2DI2WwzoAd578Fg6wI2ag9jSHEezKLuulu
POZH0zYhXnF8VntLB8w5sxRx6mSUbW/TkaxZVLj0aoYPhNSxba56Afn9ZAwUmCYH
qnq6ssCpTKXblZrtxw8jL42hqR/a06mE0M7iKofWhF2tIdmbcBRu6ixH1RWJ/t+A
SiA0LmfMssDI6f9hFulqWWHxaNSkOjT+QHlGWVoxzCImromvQSpAMbJmsp9JG8H9
qd/Nlfp0kiWwKOM0KkwM53uA0UEGFmsDIwWQkWvVmbRS/T2jRT+JSy5gd4h7Sygz
blOFFoAPAgMBAAECggEBAJdtnA/nEo3Zkn04/XWoTphZI9P05jh/REDvzzMpdkg8
fbRMWqj3cPcIBDpxkt6iRss8y3WGdd5+KVIXWBBWDgvBIHfS5irY/Vr3r8rYqO28
HPgmjP1oKNILppcMtmP9BY60bTn+rFbAun1aLPctVKB88TQyuTLeQ8zTAHscEYs5
mNrcAZRGqDy8aOBdZnmrtucjZ4wtJXsG7jdsnqSrLNEVvegBBrJqVWs8+ynMnBIj
y8XYU+0uUgJkDA1kgUK0hozqssoNU3JYylmGL5/9foTkSJ1GaAXpnYH7eEnYTpN1
sz4BJtpirbm2zbv0+5Tj/gvfvJ6z/QUFv/ac537j0mkCgYEA/4ChmBQTfBBd3ypn
KraPky3BRBxOaZCm6d18r+beuP0ZuwMs0ZoHUVA3Ps71ZrxGdPgsuQVKgsxs2UBv
O1gVG3VOXO3TF83cASZOGMyNHP0B++jiNAP/JSXFLAminXPaqS+P/Zj4adN67uBC
KJA11bxgizLuv+bZ/JH5qu9zIXUCgYEA4y5DHAP2dvVdWmmiyRo9uhtJVEKLEPi6
IDa6Sf12mrfuDEKkc5NcxuzI2gNXjGXVLDB4JITGY91VI+QS97YeTLlMiKDEi55X
Sn405KCsaiLrTy9E7AzBcsnoQjRL8f0XTAIYFpwSODUnjb6oKHPbH+UJ5BeUcqRe
tKCIR+pRBvMCgYEAixAh47oZmM73qL1VhYPzxTGEHWQisYZPsr4gXUUVOC5Z0NW7
kSF6liFI0GCoZJBY8NUa0mE02tgU7nIJmI0qf9VrH106JZyf/+gvXYQH0h1K9Scd
5x29wyQ5muxrm7Mw8iC3CFo36rF2GYnpuFY1Vu2+xkSkecJWJwf0kbreOPkCgYEA
q8+k+V8V2smeHG6fqi+qV0Gjp5Hb0q4JNauuH58NP92yrpsH/FCKbfdNv3OflpK9
MXpGone4Ana1mTs4DRcyuxu4gev0ORM7OR9RqUbKnkpiY7SAD3VmKAYDHW6nsQ+T
uuwqg47tSI0KqOx0CIP2SJzTailbH4ioBzsRVjIjrXkCgYBbViNMOLYf/u25Hndu
MeDMAR9kW7odPlDRa+IGSI1Vy2nAVGBPb2OEG0PcuxZsbgWrXH5RHNsl6yTklC8K
LZIG0vRnRp9oXnQieD9t4FRGPyo1HtUmH5tsAyehFgLIB9Wci3QxFZIX1xqr6GjH
sLDFM8t6bOUuCPJOPOCvCbX85w==
-----END PRIVATE KEY-----
controlplane $ 


# Criar o secret tls para o ingress

k -n world create secret tls world --cert=./cert.crt --key=./cert.key


# Criar um serviço para usar tls

$ k -n world create ingress novo-world --rule="sistemas.com/diplom/*=asia:80,tls=world"  --class=nginx --dry-run=client -o yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  creationTimestamp: null
  name: novo-world
  namespace: world
spec:
  ingressClassName: nginx
  rules:
  - host: sistemas.com
    http:
      paths:
      - backend:
          service:
            name: asia
            port:
              number: 80
        path: /diplom/
        pathType: Prefix
  tls:
  - hosts:
    - sistemas.com
    secretName: world

    