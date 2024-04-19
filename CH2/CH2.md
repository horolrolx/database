# Relational Algebra
- -select 선택 연산 : σ
- project 투영 연산 : π
- union 합집합 연산 : ∪
- set difference 차집합 연산 : -
- Cartesian produxt 카타시안곱 연산 : x
- rename 재명명 연산 : ρ

# 선택 연산 Selection Operation
- 시그마( σ ), 각각의 항은 ∨(or), ∧(and), ￢(not)으로 연결이 가능

# 투영 연산 Projection Operation
- 파이( π ), 중요 ! 중복 tuple은 결과관계에서 제거된다는 점

# 카타시안 곱 연산 Cartesian Product Operation
- 튜플의 모든 가능한 조합을 결과 관계로 산출함
- 각각 릴레이션의 튜플의 개수가 5, 3이라면 5 x 3해서 15개가 나와야함
- rename(재명명)

# 합집합 연산 Union Operation
- 합집합( ∪ ), 속성(attribute) 개수가 같고, 타입(type)이 compatible(같다? 호환 가능?)해야함

# 차집합 연산 Set Difference Operation
- 차집합( - ), 속성(attribute) 개수 같아야하고 compatible relations 사이에서 이루어져야함

# 교집합 연산 Set Intersection Operation
- 교집합( ∩ ), 속성(attribute) 개수가 같고, 타입(type) 상호호환 되어야함

# 자연조인 연산 Natural Join Operation
- 자연조인( ⋈ ), 카타시안 곱( X ) 수행하고, 조인조건 이용하여 선택 연산( σ ) 수행, 조인조건에 언급된 속성을 이용하여 투영 연산( π )을 수행