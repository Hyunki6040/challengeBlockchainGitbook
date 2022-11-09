---
description: 나의 인증 여부와 가장 마지막 인증 결과를 조회합니다.
---

# 인증 조회

## 인증 조회

{% swagger baseUrl="{host}" method="get" path="/certification/search" summary="Search Certification" %}
{% swagger-description %}
나의 인증 여부와 가장 마지막 인증 결과를 조회합니다.
{% endswagger-description %}

{% swagger-parameter in="body" name="challenge_no" required="true" type="string" %}
루틴 번호
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
JWT Token
{% endswagger-parameter %}

{% swagger-response status="200" description="인증 조회 완료" %}
```javascript
{
    "status": "success",
    "msg": null
    "result" : {
        "routine_no" : 1,
        "certification": "인증내용",
        "certification_date": "인증일",
        "status": "인증 상태(success, process, fail)",
        "next_certification_date": "다음 인증일"
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
&#x20;마지막 인증과 루틴에 인증을 계속 진행할 수 있는 지 여부를 조회합니다.
{% endhint %}
