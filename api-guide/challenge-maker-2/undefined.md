---
description: 투표수가 제일적은 인증 1개를 조회합니다.
---

# 투표할 인증 조회

인증일에 가장 근접하고 투표수가 제일 적은 다른 사용자의 [인증](../challenge-maker-1/)을 무작위로 조회합니다.

## 투표할 인증 조회

{% swagger baseUrl="{host}" method="get" path="/vote/get" summary="Get Certification For Vote" %}
{% swagger-description %}
투표가 필요한 다른 사용자의 인증을 조회합니다.
{% endswagger-description %}

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
        "my_vote_count": 남은 투표 횟수,
        "certification_no": "인증 번호",
        "routine_title" : "루틴명",
        "routine_certification": "인증기준",
        "certification": "인증내용",
        "certification_date": "인증일",
        "reason": "실패 사유 목록(list)"
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}
