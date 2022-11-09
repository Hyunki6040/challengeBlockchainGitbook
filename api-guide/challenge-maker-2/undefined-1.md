---
description: 타 사용자의 인증에 투표를 진행합니다.
---

# 투표하기

{% hint style="info" %}
[인증](../challenge-maker-1/) 1회에 [투표](./) 2회까지만 가능합니다.

자신의 인증 전에 투표 2회를 진행해야 하며, 인증을 업로드 해야 투표 횟수가 초기화 됩니다.
{% endhint %}

## 투표하기

{% swagger baseUrl="{host}" method="post" path="/vote/{certification_no}" summary="Vote Certification" %}
{% swagger-description %}
루틴에 해당하는 인증을 업로드합니다.
{% endswagger-description %}

{% swagger-parameter in="body" name="status" type="boolean" required="true" %}
인증 성공 여부

\


(false: 실패, true:성공)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="reason" type="string" required="false" %}
(status가 false일 때)

\


실패 사유
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
JWT Token
{% endswagger-parameter %}

{% swagger-response status="200" description="투표 완료" %}
```javascript
{
    "status": "success",
    "msg": "투표가 완료되었습니다."
    "result" : {
        "my_vote_count": 남은 투표 횟수
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}
