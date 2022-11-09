---
description: 생성된 루틴의 정보를 수정, 삭제합니다.
---

# 루틴 수정, 삭제

{% hint style="warning" %}
Routine의 수정과 삭제는 Routine가 시작되기 전에만 할 수 있습니다.
{% endhint %}

## Routine 수정

{% swagger baseUrl="{host}" method="put" path="/routine/update/{routine_no}" summary="updateRoutine" %}
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

{% swagger-response status="200" description="루틴 수정완료" %}
```javascript
{
    "status": "success",
    "msg": "루틴이 수정되었습니다.",
    "result" : {
        "routine_no" : 1
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
모든 Routine는 Smart Contract에 배포되므로 "인증방식" 부분만 수정 가능합니다.
{% endhint %}

## Routine 삭제

{% swagger baseUrl="{host}" method="delete" path="/routine/delete/{routine_no}" summary="delete Routine" %}
{% swagger-description %}
Challenge를 삭제합니다.
{% endswagger-description %}

{% swagger-parameter in="body" name="reason" type="string" required="true" %}
루틴 취소 사유
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
JWT Token
{% endswagger-parameter %}

{% swagger-response status="200" description="루틴 삭제완료" %}
```javascript
{
    "status": "success",
    "msg": "루틴이 수정되었습니다.",
    "result" : null
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="danger" %}
모든 Routine은 Smart Contract로 처리됩니다.&#x20;

루틴 취소 시 작성한 사유가 참가자들에게 공유되고 참가비를 환불합니다.
{% endhint %}
