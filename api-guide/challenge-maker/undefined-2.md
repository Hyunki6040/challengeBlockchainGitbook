---
description: 생성된 챌린지의 정보를 수정, 삭제합니다.
---

# 챌린지 수정, 삭제

{% hint style="warning" %}
Challenge의 수정과 삭제는 Challenge가 시작되기 전에만 할 수 있습니다.
{% endhint %}

## Challenge 수정

{% swagger baseUrl="{host}" method="put" path="/challenge/update/{challenge_no}" summary="update Challenge" %}
{% swagger-description %}
Challenge를 수정합니다.
{% endswagger-description %}

{% swagger-parameter in="body" name="certification" type="string" required="true" %}
인증 방식설명
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
JWT Token
{% endswagger-parameter %}

{% swagger-response status="200" description="챌린지 수정완료" %}
```javascript
{
    "status": "success",
    "msg": "챌린지가 수정되었습니다.",
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
모든 Challenge는 Smart Contract에 배포되므로 "인증방식" 부분만 수정 가능합니다.
{% endhint %}

## Challenge 삭제

{% swagger baseUrl="{host}" method="delete" path="/challenge/delete/{challenge_no}" summary="delete Challenge" %}
{% swagger-description %}
Challenge를 삭제합니다.
{% endswagger-description %}

{% swagger-parameter in="body" name="reason" type="string" required="true" %}
챌린지 취소 사유
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
JWT Token
{% endswagger-parameter %}

{% swagger-response status="200" description="챌린지 삭제완료" %}
```javascript
{
    "status": "success",
    "msg": "챌린지가 수정되었습니다.",
    "result" : null
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="danger" %}
모든 Challenge는 Smart Contract로 처리됩니다.&#x20;

챌린지 취소 시 작성한 사유가 참가자들에게 공유되고 참가비를 환불합니다.
{% endhint %}
