---
description: 챌린지에 인증을 업로드합니다.
---

# 인증 업로드

{% hint style="danger" %}
다른 사용자의 인증 2개를 [투표](../challenge-maker-2/)해야 자신의 인증을 업로드할 수 있습니다.&#x20;

악의적인 투표시, 자신의 인증도 무효처리됩니다.
{% endhint %}

## 인증 업로드

{% swagger baseUrl="{host}" method="post" path="/certification/upload" summary="Upload Certification" %}
{% swagger-description %}
챌린지에 해당하는 인증을 업로드합니다.
{% endswagger-description %}

{% swagger-parameter in="body" name="challenge_no" required="true" type="string" %}
챌린지 번호
{% endswagger-parameter %}

{% swagger-parameter in="body" name="certification" type="string" %}
인증 내용
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
    "msg": null
    "result" : {
        "certification_no" : 1,
        "next_certification_date": "다음 인증일"
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}
