# Search Engines @0xAwali

### Discovering Dashboards

- **SHODAN**
    
    `**hostname:company.com dashboard**`
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" http.title:"dashboard"`** 
    
    `**ssl:"[company.com](http://company.com/)" http.title:"dashboard"**`
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" dashboard**`
    
    `**ssl:"[company.com](http://company.com/)" dashboard**`
    
    `**asn:ASN Number e.g. AS19551+http.title:"dashboard”**`
    
    `**asn:ASN Number e.g. AS19551+dashboard**`
    
    `**hostname:company.com http.title:dashboard**`
    
    `**net:"I.P.v.4/CIDR" http.title:dashboard**`
    
    `**net:"I.P.v.4/CIDR" dashboard**`
    
    `**org:"Company Inc" http.title:dashboard**`
    
- **FOFA**
    
    `**cert="[company.com](http://company.com/)" && title="dashboard"**`
    
    `**cert.subject="company" && title="dashboard”**`
    
    `**cert="[company.com](http://company.com/)" && body="dashboard"**`
    
    `**cert.subject="company" && body="dashboard”**`
    
    `**asn="Number e.g. 19551" && title="dashboard”**`
    
    `**asn="Number e.g. 19551" && body="dashboard”**`
    
    `**domain="[company.com](http://company.com/)" && title="dashboard"**`
    
    `**domain="[company.com](http://company.com/)" && body="dashboard"**`
    
    `**ip="I.P.v.4/CIDR" && title="dashboard”**`
    
    `**ip="I.P.v.4/CIDR" && body="dashboard”**`
    
    `**org="Company Name Inc." && title="dashboard”**`
    
- **GOOGLE**
    
    `**site:*.company.com intitle:"dashboard”**`
    

---

### Sign Up Pages

- **SHODAN**
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" http.title:"sign up"**`
    
    `**ssl:"[company.com](http://company.com/)" http.title:"sign up"**`
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" "sign up"[ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" "sign up"**`
    
    `**ssl:"[company.com](http://company.com/)" "sign up"**`
    
    `**asn:ASN Number e.g. AS19551+http.title:"sign up”**`
    
    `**asn:ASN Number e.g. AS19551+"sign up”**`
    
    `**hostname:company.com "sign up”**`
    
    `**hostname:company.com http.title:"sign up”**`
    
    `**net:"I.P.v.4/CIDR" http.title:"sign up”**`
    
    `**net:"I.P.v.4/CIDR" "sign up”**`
    
    `**org:"Company Inc" http.title:"sign up”**`
    
    `**org:"Company Inc" "sign up”**`
    
- **FOFA**
    
    `**cert="[company.com](http://company.com/)" && title="sign up"**`
    
    `**cert.subject="company" && title="sign up”**`
    
    `**cert="[company.com](http://company.com/)" && body="sign up"**`
    
    `**cert.subject="company" && body"sign up”**`
    
    `**asn="Number e.g. 19551" && title="sign up”**`
    
    `**domain="[company.com](http://company.com/)" && body="sign up"**`
    
    `**ip="I.P.v.4/CIDR" && title="sign up”**`
    
    `**org="Company Name Inc." && body="sign up”**`
    
- **GOOGLE**
    
    `**site:*.company.com intitle:"sign up”**`
    

---

### Login Pages

- **SHODAN**
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" http.title:"log in"**`
    
    `**ssl:"[company.com](http://company.com/)" http.title:"log in"**`
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" "log in"**`
    
    `**ssl:"[company.com](http://company.com/)" "log in"**`
    
    `**asn:ASN Number e.g. AS19551+http.title:"log in”**`
    
    `**asn:ASN Number e.g. AS19551+"log in”**`
    
    `**hostname:company.com http.title:"log in”**`
    
    `**hostname:company.com "log in”**`
    
    `**net:"I.P.v.4/CIDR" http.title:"log in”**`
    
    `**net:"I.P.v.4/CIDR" "log in”**`
    
    `**org:"Company Inc" http.title:"log in”**`
    
    `**org:"Company Inc" "log in”**`
    
- **FOFA**
    
    `**cert="[company.com](http://company.com/)" && title="log in"
    cert.subject="company" && title="log in”**`
    
    `**cert="[company.com](http://company.com/)" && body="log in"**`
    
    `**cert.subject="company" && body="log in”**`
    
    `**asn="Number e.g. 19551" && title="log in”**`
    
    `**domain="[company.com](http://company.com/)" && title="log in"**`
    
    `**asn="Number e.g. 19551" && body="log in”**`
    
    `**domain="[company.com](http://company.com/)" && body="log in"**`
    
    `**ip="I.P.v.4/CIDR" && title="log in”**`
    
    `**ip="I.P.v.4/CIDR" && body="log in”**`
    
    `**org="Company Name Inc." && title="log in”**`
    
    `**org="Company Name Inc." && body="log in”**`
    
- **GOOGLE**
    
    `**site:*.company.com intitle:"log in”**`
    

---

### OAuth Pages

- **SHODAN**
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" http.title:"log in with"**`
    
    `**ssl:"[company.com](http://company.com/)" http.title:"log in with"**`
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" http.status:302 oauth**`
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" oauth**`
    
    `**ssl:"[company.com](http://company.com/)" http.status:302 oauth**`
    
    `**ssl:"[company.com](http://company.com/)" oauth**`
    
    `**asn:ASN Number e.g. AS19551+http.title:"log in with”**`
    
    `**asn:ASN Number e.g. AS19551 http.status:302 oauth**`
    
    `**asn:ASN Number e.g. AS19551+"log in with”**`
    
    `**hostname:company.com http.title:"log in with”**`
    
    `**hostname:company.com http.status:302 oauth**`
    
    `**hostname:company.com "log in with”**`
    
    `**net:"I.P.v.4/CIDR" http.title:"log in with”**`
    
    `**net:"I.P.v.4/CIDR" http.status:302 oauth**`
    
    `**net:"I.P.v.4/CIDR" "log in with”**`
    
    `**org:"Company Inc" http.title:"log in with”**`
    
    `**org:"Company Inc" http.status:302 oauth**`
    
    `**org:"Company Inc" oauth**`
    
- **FOFA**
    
    `**cert="[company.com](http://company.com/)" && title="log in with"**`
    
    `**cert.subject="company" && title="log in with”**`
    
    `**cert.subject="company" && body="oauth”**`
    
    `**cert="[company.com](http://company.com/)" && body="oauth"**`
    
    `**asn="Number e.g. 19551" && title="log in with”**`
    
    **`asn="Number" && status_code="302" && header="oauth”`**
    
    `**asn="Number e.g. 19551" && body="log in with”**`
    
    `**domain="[company.com](http://company.com/)" && title="log in with"**`
    
    `**domain="[company.com](http://company.com/)" && status_code="302" && header="oauth"**`
    
    `**domain="[company.com](http://company.com/)" && body="log in with"**`
    
    `**ip="I.P.v.4/CIDR" && title="log in”**`
    
    `**ip="I.P.v.4/CIDR" && status_code="302" && header="oauth”**`
    
    `**ip="I.P.v.4/CIDR" && body="log in”**`
    
    `**org="Company Name Inc." && title="log in with”**`
    
    `**org="Company Name Inc." && status_code="302" && header="oauth”**`
    
    `**org="Company Name Inc." && body="oauth”**`
    
- **GOOGLE**
    
    `**site:*.company.com intitle:"log in with”**`
    

---

### Single Sign-On Pages

- **SHODAN**
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" http.title:"login sso"**`
    
    `**ssl:"[company.com](http://company.com/)" http.title:"login sso"**`
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" http.status:302 sso**`
    
    `**ssl:"[company.com](http://company.com/)" http.status:302 sso**`
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" "login sso"**`
    
    `**ssl:"[company.com](http://company.com/)" "login sso"**`
    
    `**asn:ASN Number e.g. AS19551+http.title:"sso”**`
    
    `**asn:ASN Number e.g. AS19551 http.status:302 sso**`
    
    `**asn:ASN Number e.g. AS19551+sso**`
    
    `**hostname:company.com http.title:"sso”**`
    
    `**hostname:company.com http.status:302 sso**`
    
    `**hostname:company.com sso**`
    
    `**net:"I.P.v.4/CIDR" http.title:"sso”**`
    
    `**net:"I.P.v.4/CIDR" http.status:302 sso**`
    
    `**net:"I.P.v.4/CIDR" sso**`
    
    `**org:"Company Inc" http.title:"sso”**`
    
    `**org:"Company Inc" http.status:302 sso**`
    
    `**org:"Company Inc" sso**`
    
- **FOFA**
    
    **`cert="[company.com](http://company.com/)" && title="login sso"`**
    
    `**cert.subject="company" && title="login sso”**`
    
    `**cert="[company.com](http://company.com/)" && status_code="302" && header="sso"**`
    
    `**cert.subject="company" && status_code="302" && header="sso”**`
    
    `**cert="[company.com](http://company.com/)" && body="login sso"**`
    
    `**cert.subject="company" && body="login sso”**`
    
    `**asn="Number e.g. 19551" && title="sso”**`
    
    `**asn="Number" && status_code="302" && header="sso”**`
    
    `**asn="Number e.g. 19551" && body="sso”**`
    
    `**domain="[company.com](http://company.com/)" && title="sso"**`
    
    `**domain="[company.com](http://company.com/)" && status_code="302" && header="sso"**`
    
    `**domain="[company.com](http://company.com/)" && body="sso"**`
    
    `**ip="I.P.v.4/CIDR" && title="sso”**`
    
    `**ip="I.P.v.4/CIDR" && status_code="302" && header="sso”**`
    
    `**ip="I.P.v.4/CIDR" && body="sso”**`
    
    `**org="Company Name Inc." && title="sso”**`
    
    `**org="Company Name Inc." && status_code="302" && header="sso”**`
    
    `**org="Company Name Inc." && body="sso”**`
    
- **GOOGLE**
    
    `**site:*.company.com intitle:"sso”**`
    

---

### Reset Password Pages

- **SHODAN**
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" http.title:"password"**`
    
    `**ssl:"[company.com](http://company.com/)" http.title:"password"**`
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" "reset pass"**`
    
    `**ssl:"[company.com](http://company.com/)" "reset pass"**`
    
    `**asn:ASN Number e.g. AS19551+http.title:"password”**`
    
    `**asn:ASN Number e.g. AS19551+"reset pass”**`
    
    `**hostname:company.com "reset pass”**`
    
    `**net:"I.P.v.4/CIDR" http.title:"password”**`
    
    `**net:"I.P.v.4/CIDR" "reset pass”**`
    
    `**org:"Company Inc" http.title:"password”**`
    
    `**org:"Company Inc" "password”**`
    
- **FOFA**
    
    `**cert="[company.com](http://company.com/)" && title="password"**`
    
    `**cert.subject="company" && title="password”**`
    
    `**cert="[company.com](http://company.com/)" && body="reset pass"**`
    
    `**cert.subject="company" && body="reset pass”**`
    
    `**asn="Number e.g. 19551" && title="password”**`
    
    `**asn="Number e.g. 19551" && body="reset pass”**`
    
    `**hostname:company.com http.title:"password”**`
    
    `**domain="[company.com](http://company.com/)" && title="password"**`
    
    `**domain="[company.com](http://company.com/)" && body="password"**`
    
    `**ip="I.P.v.4/CIDR" && title="password”**`
    
    `**ip="I.P.v.4/CIDR" && body="reset pass”**`
    
    `**org="Company Name Inc." && title="password”**`
    
    `**org="Company Name Inc." && body="password”**`
    
- **GOOGLE**
    
    `**site:*.company.com intitle:"password”**`
    

---

### File Upload Pages

- **SHODAN**
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" http.title:"upload"**`
    
    `**ssl:"[company.com](http://company.com/)" http.title:"upload"**`
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" "upload"**`
    
    `**ssl:"[company.com](http://company.com/)" "upload"**`
    
    `**asn:ASN Number e.g. AS19551+http.title:"upload”**`
    
    `**asn:ASN Number e.g. AS19551+"upload”**`
    
    `**hostname:company.com http.title:"upload”**`
    
    `**hostname:company.com "upload”**`
    
    `**net:"I.P.v.4/CIDR" http.title:"upload”**`
    
    `**net:"I.P.v.4/CIDR" "upload”**`
    
    `**org:"Company Inc" http.title:"upload”**`
    
    `**org:"Company Inc" "upload”**`
    
- **FOFA**
    
    `**cert="[company.com](http://company.com/)" && title="upload"**`
    
    `**cert.subject="company" && title="upload”**`
    
    `**cert="[company.com](http://company.com/)" && body="upload"**`
    
    `**cert.subject="company" && body="upload”**`
    
    `**asn="Number e.g. 19551" && title="upload”**`
    
    `**asn="Number e.g. 19551" && body="upload”**`
    
    `**domain="[company.com](http://company.com/)" && title="upload"**`
    
    `**domain="[company.com](http://company.com/)" && body="upload"**`
    
    `**ip="I.P.v.4/CIDR" && title="upload”**`
    
    `**ip="I.P.v.4/CIDR" && body="upload”**`
    
    `**org="Company Name Inc." && title="upload”**`
    
    `**org="Company Name Inc." && body="upload”**`
    
- **GOOGLE**
    
    site:*.company.com intitle:"upload”
    

---

### Settings Pages

- **SHODAN**
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" http.title:"settings"**`
    
    `**ssl:"[company.com](http://company.com/)" http.title:"settings"**`
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" "settings"**`
    
    `**ssl:"[company.com](http://company.com/)" "settings"**`
    
    `**asn:ASN Number e.g. AS19551+http.title:"settings”**`
    
    `**asn:ASN Number e.g. AS19551+"settings”**`
    
    `**hostname:company.com http.title:"settings”**`
    
    `**hostname:company.com "settings”**`
    
    `**net:"I.P.v.4/CIDR" http.title:"settings”**`
    
    `**net:"I.P.v.4/CIDR" "settings”**`
    
    `**org:"Company Inc" http.title:"settings”**`
    
    `**org:"Company Inc" "settings”**`
    
- **FOFA**
    
    `**cert="[company.com](http://company.com/)" && title="settings"**`
    
    `**cert.subject="company" && title="settings”**`
    
    `**cert="[company.com](http://company.com/)" && body="settings"**`
    
    `**cert.subject="company" && body="settings”**`
    
    `**asn="Number e.g. 19551" && title="settings”**`
    
    `**asn="Number e.g. 19551" && body="settings”**`
    
    `**domain="[company.com](http://company.com/)" && title="settings"**`
    
    `**domain="[company.com](http://company.com/)" && body="settings"**`
    
    `**ip="I.P.v.4/CIDR" && title="settings”**`
    
    `**ip="I.P.v.4/CIDR" && body="settings”**`
    
    `**org:"Company Inc" http.title:"settings”**`
    
    `**org="Company Name Inc." && body="settings”**`
    
- **GOOGLE**
    
    domain="[company.com](http://company.com/)" && body="settings"
    

---

### Contact Support Pages

- **SHODAN**
    
    [`**ssl.cert.subject.cn](http://ssl.cert.subject.cn/):"[company.com](http://company.com/)" http.title:"support"**`
    
    `**ssl:"[company.com](http://company.com/)" http.title:"support"**`
    
    `**cert.subject="company" && title="support”**`
    
    `**ssl:"[company.com](http://company.com/)" "support"**`
    
    `**asn:ASN Number e.g. AS19551+http.title:"support”**`
    
    `**asn:ASN Number e.g. AS19551+"support”**`
    
    `**hostname:company.com http.title:"support”**`
    
    `**hostname:company.com "support”**`
    
    `**net:"I.P.v.4/CIDR" http.title:"support”**`
    
- **FOFA**
    
    `**cert="[company.com](http://company.com/)" && title="support"**`
    
    `**cert.subject="company" && title="support”**`
    
    `**cert="[company.com](http://company.com/)" && body="support"**`
    
    `**cert.subject="company" && body="support”**`
    
    `**asn="Number e.g. 19551" && title="support”**`
    
    `**asn="Number e.g. 19551" && body="support”**`
    
    `**domain="[company.com](http://company.com/)" && title="support"**`
    
    `**ip="I.P.v.4/CIDR" && title="support”**`
    
    `**domain="[company.com](http://company.com/)" && body="support"**`
    
- **GOOGLE**
    
    `**site:*.company.com intitle:"support”**`
    

# 🍖 Bonus

[AllAboutBugBounty/Shodan Dorks.md at master · daffainfo/AllAboutBugBounty](https://github.com/daffainfo/AllAboutBugBounty/blob/master/Reconnaissance/Shodan%20Dorks.md)

[AllAboutBugBounty/Google Dorks.md at master · daffainfo/AllAboutBugBounty](https://github.com/daffainfo/AllAboutBugBounty/blob/master/Reconnaissance/Google%20Dorks.md)

**[@sl4x0](https://www.facebook.com/sl4x0/)**
