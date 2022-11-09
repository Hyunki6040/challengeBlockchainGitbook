---
description: 루틴 관련된 정보를 (다건, 단건) 조회합니다.
---

# 루틴 조회

## Routine 단건 조회

{% swagger baseUrl="{host}" method="get" path="/routine/search/{routine_no}" summary="Create Routine" %}
{% swagger-description %}
Routine 정보를 조회합니다.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
JWT Token
{% endswagger-parameter %}

{% swagger-response status="200" description="루틴 검색 결과" %}
```javascript
{
    "status": "success",
    "msg": null,
    "result" : [
        {
            "routine_no" : 1,
            "title": "루틴명",
            "description": "루틴 설명",
            "status": "루틴 상태 (proceed, start, end)",
            "certification": "인증 방식설명",
            "certification_day": [1,2,3],
            "certification_hour": 인증 시간,
            "certification_minute": 인증 분,
            "skeleton": "최소인원",
            "fee": 참가비 (KLAY),
            "start": "루틴 시작일",
            "end": "루틴 종료일",
            "maker": "루틴 생성자 Wallet 주소"
            "create_date": "루틴 생성일",
            "participants": "루틴 참가자 명단",
            "contract_address": "루틴 Contract 주소"
        },
        ...
    ]
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}

## Routine다건 조회

{% swagger baseUrl="{host}" method="get" path="/routine/search" summary="Create Routine" %}
{% swagger-description %}
Routine 정보를 조회합니다.
{% endswagger-description %}

{% swagger-parameter in="body" type="date" name="start" required="false" %}
루틴 시작일

\


(

`null`

이면, 오늘로 검색)
{% endswagger-parameter %}

{% swagger-parameter in="body" required="false" name="end" type="date" %}
루틴 종료일

\


(

`null`

이면, 오늘로 검색)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="keyword" required="false" type="string" %}
루틴명

\


(포함 문자 검색)
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="true" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
JWT Token
{% endswagger-parameter %}

{% swagger-parameter in="body" type="string" name="status" %}
루틴 상태 (proceed, start, end)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="fee" type="double" required="false" %}
참가비 (KLAY)
{% endswagger-parameter %}

{% swagger-response status="200" description="루틴 검색 결과" %}
```javascript
{
    "status": "success",
    "msg": null,
    "result" : [
        {
            "routine_no" : 1,
            "title": "루틴명",
            "description": "루틴 설명",
            "status": "루틴 상태 (proceed, start, end)",
            "certification": "인증 방식설명",
            "certification_day": [1,2,3],
            "certification_hour": 인증 시간,
            "certification_minute": 인증 분,
            "skeleton": "최소인원",
            "fee": 참가비 (KLAY),
            "start": "루틴 시작일",
            "end": "루틴 종료일",
            "maker": "루틴 생성자 Wallet 주소"
            "create_date": "루틴 생성일",
            "participants": "루틴 참가자 명단",
            "contract_address": "루틴 Contract 주소"
        },
        ...
    ]
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}
