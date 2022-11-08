---
description: 챌린지에 업로드한 인증을 수정/삭제합니다.
---

# 인증 수정/삭제

{% hint style="danger" %}
인증의 수정/삭제시 모든 투표수가 초기화 되며, 인증 종료 24시간 전에만 가능합니다.
{% endhint %}

## 인증 수정

{% swagger baseUrl="{host}" method="put" path="/certification/update/{certification_no}" summary="update Certification" %}
{% swagger-description %}
인증을 수정합니다.
{% endswagger-description %}

{% swagger-parameter in="body" name="certification" type="string" required="true" %}
인증내용
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
JWT Token
{% endswagger-parameter %}

{% swagger-response status="200" description="인증 업로드 완료" %}
```javascript
{
    "status": "success",
    "msg": "인증이 수정되었습니다.",
    "result" : {
        "certification_no" : 1
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}

## 인증 삭제

{% swagger baseUrl="{host}" method="delete" path="/certification/delete/{certification_no}" summary="delete Certification" %}
{% swagger-description %}
인증을 수정합니다.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
JWT Token
{% endswagger-parameter %}

{% swagger-response status="200" description="인증 업로드 완료" %}
```javascript
{
    "status": "success",
    "msg": "인증이 삭제되었습니다.",
    "result" : null
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}
