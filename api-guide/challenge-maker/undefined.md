---
description: 챌린지를 생성하고 관련된 contract를 실행해 Blockchain에 기록합니다.
---

# 챌린지 생성

## Challenge 생성

{% swagger baseUrl="{host}" method="post" path="/challenge/create" summary="Create Challenge" %}
{% swagger-description %}
Challenge를 생성합니다.
{% endswagger-description %}

{% swagger-parameter in="body" name="title" required="true" type="string" %}
챌린지명
{% endswagger-parameter %}

{% swagger-parameter in="body" name="description" required="true" type="string" %}
챌린지 설명
{% endswagger-parameter %}

{% swagger-parameter in="body" name="certification" type="string" required="true" %}
인증 방식설명
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="body" name="certification_day" type="int[]" required="true" %}
인증 요일

\


(1:월요일 ~ 7:일요일)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="certification_hour" type="int" required="true" %}
인증 시간

\


(0~23)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="certification_minute" type="int" required="true" %}
인증 분

\


(0~59)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="skeleton" type="Long" required="true" %}
최소인원
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
JWT Token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="fee" type="double" required="true" %}
참가비 (KLAY)
{% endswagger-parameter %}

{% swagger-parameter in="body" type="date" name="start" required="true" %}
챌린지 시작일
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="end" type="date" %}
챌린지 종료일
{% endswagger-parameter %}

{% swagger-response status="200" description="챌린지 생성완료" %}
```javascript
{
    "status": "success",
    "msg": "챌린지가 생성되었습니다.",
    "result" : {
        "challenge_no" : 1
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
매 Challenge마다 Klaytn Network에 Smart Contract 배포됩니다.&#x20;

챌린지에 참가할 참가자들은 참가비에 해당하는 KLAY를 Contract에 입금을 진행합니다.&#x20;

Smart Contract에서 챌린지 성공/실패 여부가 관리되며, 챌린지 종료후 자동으로 금액을 배분합니다.
{% endhint %}
