# JWT 인증

## **JWT 인증 과정**

![jwt process](https://cloud.githubusercontent.com/assets/9030565/21639528/e53e01ee-d2b3-11e6-86d1-6c67c16841eb.PNG)

## JWT Token 가져오기

{% swagger baseUrl="{host}" method="post" path="/login" summary="Get JWT Token" %}
{% swagger-description %}
자신의 Wallet Address와 Address를 메시지로 서명한 Message를 보내 JWT Token을 확인합니다.
{% endswagger-description %}

{% swagger-parameter in="body" name="address" required="true" type="string" %}
Wallet Address
{% endswagger-parameter %}

{% swagger-parameter in="body" name="signed_message" required="true" type="string" %}
자신의 

`address`

를 Message로 sign한 message
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-response status="200" description="Get JWT Token successfully" %}
```javascript
{
    token : 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c'
}
```
{% endswagger-response %}

{% swagger-response status="204: No Content" description="Invalid Wallet Address" %}
```javascript
{
    "status": "fail",
    "msg": "잘못된 Address입니다."
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
이후 사용자의 요청을 보낼 때 Header에 JWT Token을 포함합니다.
{% endhint %}
