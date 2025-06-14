# 트라이(Trie)란

트라이의 개념을 알아보기 전에, 트리의 개념을 간단하게 알아본다.

# 트리(Tree)란

컴퓨터 과학에서 **트리**는 계층적인 구조를 표현하기 위해 널리 사용되는 추상 자료형이다.
트리는 **노드**들의 집합으로 이루어지며, 이 노드들은 서로 연결되어 **계층 구조** 를 형성한다.

트리에서 각 노드는 자식 노드를 여러 개 가질 수 있지만, 반드시 부모 노드는 하나만 가져야 한다.
단, **루트 노드** 는 예외로, 부모가 없는 최상위 노드이다.

이러한 규칙 덕분에 트리에는 **순환** 이나 **루프**가 존재하지 않으며, 어떤 노드도 자기 자신의 조상이 될 수 없다.

<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5f/Tree_%28computer_science%29.svg/500px-Tree_%28computer_science%29.svg.png" width="180" height="200"/>
  <p style="font-size: 10px;">Tree 구조의 모습</p>
</div>

# 트라이의 정의

트라이는, 사전(dictionary)이나 집합(set)에 있는 문자열을 저장하고 검색하는 데 사용되는 특수한 탐색 트리 자료구조이다.

트라이 자료 구조는 문자열들의 집합을 저장하고, 이들에 대해 효율적인 검색, 삽입(insert), 삭제(delete), 접두사 검색(prefix search), 그리고 모든 문자열을 정렬된 순서대로 순회(sorted traversal)하는 기능을 제공하는 트리 기반 자료 구조이다. “Trie”라는 이름은 reTRIEval(검색, 회수)의 중간 부분에서 유래한 것으로, 무언가를 찾아내거나 얻어낸다는 의미를 내포하고 있다.

# 트라이의 구조

이진 탐색 트리(binary search tree)와는 달리, 트라이의 노드는 자신과 연관된 키(key)를 저장하지 않는다.

대신 각 노드의 트라이 내 위치가 해당 키를 결정하며, 노드 간의 연결은 전체 키가 아니라 개별 문자(character)에 의해 정의된다.

트라이 자료 구조의 중요한 특징 중 하나는 두 문자열이 공통 접두사(prefix)를 가질 경우, 해당 접두사에 해당하는 경로가 트리 내에서 공유된다는 점이다.

예를 들어 “apple”과 “application”이라는 두 단어가 “app”이라는 공통 접두사를 가진다면, 트라이에서 이 두 문자열의 “app”에 해당하는 노드들은 같은 조상을 공유하게 된다.
이러한 구조 덕분에 특정 접두사로 시작하는 모든 단어를 빠르게 찾아낼 수 있다.

모든 자식 노드는 부모 노드와 공통된 접두사를 가지며, 루트 노드는 빈 문자열(empty string)을 나타냅니다.

트라이는 일반적으로 문자 문자열(character string)을 저장하지만, 숫자의 순열(permutations of digits)이나 도형의 배열(shapes)과 같은 임의의 순서가 있는 요소들의 시퀀스(sequence)에도 적용할 수 있다.

트라이의 변형 중 하나는 비트 단위 트라이(bitwise trie)로, 이는 정수(integer)나 메모리 주소(memory address) 같은 고정 길이 이진 데이터의 개별 비트(bit)를 키로 사용한다.

<div align="center">
  <img src="https://media.geeksforgeeks.org/wp-content/uploads/20220828232752/Triedatastructure1.png" width="350"/>
  <p style="font-size: 10px;">Trie 자료구조</p>
</div>

# Trie는 어디에 사용되고, 왜 필요한가?

Trie 자료 구조는 데이터를 저장하고 검색하기 위해 사용됩니다. 이러한 작업은 해시 테이블(Hash Table) 같은 다른 자료 구조를 사용해서도 수행할 수 있지만, Trie는 이러한 연산을 해시 테이블보다 더 효율적으로 수행할 수 있다.

Trie(트라이) 자료 구조는 자동 완성(autocomplete), 철자 검사(spell checking), IP 라우팅(IP routing)과 같은 작업에 특히 효과적이다.

# Trie 자료구조를 사용한 알고리즘

1. **자동 완성 기능(Autocomplete Feature)**

   - 사용자가 검색 상자에 입력하는 내용에 따라 추천 결과를 제공합니다. Trie 자료 구조는 자동 완성 기능을 구현하는 데 사용된다.

<div align="center">
  <img src="./assets/Trie/autocompletion.png", width="300"/>
  <p style="font-size: 10px;">Trie 자료구조를 활용한 자동완성 기능</p>
</div>

2. **맞춤법 검사(Spell Checkers)**

   - 사용자가 입력한 단어가 사전에 없으면, 입력한 문자열을 기반으로 제안 목록을 생성한다.

   - 다음과 같은 과정을 거친다.

     1. 사전에 단어가 존재하는지 확인
     2. 가능한 제안 후보 생성
     3. 우선순위에 따라 제안 결과 정렬

   - Trie는 단어 사전을 저장하여 단어 검색을 빠르게 수행하고, 유효한 단어 목록을 제공하는 알고리즘 구현을 용이하게 해준다.

3. **최장 접두사 일치 알고리즘(Longest Prefix Matching Algorithm)**

   - 네트워크 장치(IP 라우터)에서 네트워크 경로 최적화를 위해 사용된다. URL 주소(또는 IP 주소) 주소를 비트 단위로 연속적으로 마스킹(masking)하며, O(n) 시간 복잡도로 탐색을 수행한다.

   - 다단계 비트 트라이(Multi-Bit Trie) 기법이 개발되어 여러 비트를 한 번에 조회함으로써 탐색 속도를 더욱 향상시킬 수 있다.

# 트라이의 구현 방식

트라이의 구현 방식에는 노드를 어떻게 구현하느냐에 따라 달라진다. 방식은 여러 가지가 존재하는데, 이곳에서는 대표적인 두 가지 방식을 소개한다.

## 배열

<div align="center">
  <img src="./assets/Trie/trie-node-array.png" width=550"/>
  <p style="font-size: 10px;">Trie의 노드 Array 구현 방식</p>
</div>

배열로 구현하는 방식은, 각 자식

## 해시 맵

<div align="center">
  <img src="./assets/Trie/trie-node-hash-table.png" width=550"/>
  <p style="font-size: 10px;">Trie의 노드 Hash Map 구현 방식</p>
</div>

해시 맵으로 구현하는 방식은,

# Trie 자료구조의 시간복잡도, 공간복잡도

## 시간 복잡도

| 연산   | 평균 시간 복잡도 | 최악 시간 복잡도 |
| :----- | :--------------: | ---------------: |
| Search |   $\Theta(L)$    |      $\Theta(L)$ |
| Insert |   $\Theta(L)$    |      $\Theta(L)$ |
| Delete |   $\Theta(L)$    |      $\Theta(L)$ |

- $L$: 키(문자열)의 길이

## 공간 복잡도

|  구현 방식  | 최악 공간 복잡도                                        | 평균(실용) 공간 복잡도                                  |
| :---------: | :------------------------------------------------------ | :------------------------------------------------------ |
|  배열 기반  | $O\bigl(N \cdot L \cdot \Sigma\bigr)$                   | $O\bigl(N \cdot L \cdot \Sigma\bigr)$                   |
| 해시맵 기반 | $O\Bigl(\sum_{i=1}^{N} \lvert \text{key}_i\rvert\Bigr)$ | $O\Bigl(\sum_{i=1}^{N} \lvert \text{key}_i\rvert\Bigr)$ |

- $N$: 저장된 키의 개수
- $L$: 키(문자열)의 길이
- $\Sigma$: 알파벳(문자 집합)의 크기

**배열 기반 vs 해시맵 기반의 차이**

- **배열 기반 구현**:
  - 각 노드가 항상 $\Sigma$ 크기의 포인터 배열을 가지므로, 노드 수(≈저장된 모든 문자열 길이의 합)에 비례하여 고정된 공간을 사용한다.
  - 예를 들어 알파벳이 26종일 때, 노드가 30개라면 전체 포인터 수는 $30 \times 26 = 780$개가 된다.
- **해시맵 기반 구현**:
  - 각 노드는 실제 자식 문자만큼만 해시 엔트리를 할당하므로, 삽입된 총 문자 수만큼의 공간을 사용한다.
  - 최악의 경우에도 노드 수가 약 30개라고 해도, 실제 엣지(edge) 개수는 삽입된 모든 키의 문자 합계(≈24) 정도만 사용하게 된다.

### 간단한 예시 (배열 vs 해시맵)

- 알파벳 $\Sigma = 26$개 (영소문자 a–z), 저장할 키 5개(각각의 길이는 4~6 가정한다)로 가정한다.

  1. **배열 기반**
     - 최악(공유 없음)의 경우에는 다음과 같이 계산된다.
       - 노드 수 ≈ $5 \times 6 = 30$
     - 각 노드가 26개 포인터를 가진다고 가정했을 때, 다음과 같이 계산된다.
       - 전체 포인터 개수 = $30 \times 26 = 780$
     - 공간 복잡도는 다음과 같이 계산될 수 있다.
       - $O(\text{노드 수} \times \Sigma) = O(N \cdot L \cdot \Sigma)$
  2. **해시맵 기반**
     - 최악 노드 수 ≈ $30$이지만, 실제 자식은 평균 2~3개 문자만 존재한다고 가정하면 다음과 같이 계산될 수 있다.
       - 전체 엣지 수 ≈ $\sum_{i=1}^5 \lvert \text{key}_i\rvert = 4 + 5 + 6 + 4 + 5 = 24$
     - 각 노드는 실제 엣지 개수만큼만 해시 엔트리를 가지므로 다음과 같이 계산될 수 있다.
       - 전체 포인터(해시 버킷) 개수 ≈ $24$ (약간의 해시 오버헤드 포함)
     - 공간 복잡도는 다음과 같다.
       - $O\bigl(\sum_{i=1}^N \lvert \text{key}_i\rvert\bigr) \approx O(N \cdot L)$

- **배열 기반 구현**은 빠른 탐색(상수 시간 인덱싱)이 장점이지만, 알파벳 수($\Sigma$)가 클수록(예: 한글, 이모지 등) 메모리 낭비가 심해질 수 있다.
- **해시맵 기반 구현**은 메모리를 절약할 수 있으나, 해시 충돌 처리나 해시 함수 계산 오버헤드가 발생할 수 있다.

### References

- https://www.geeksforgeeks.org/introduction-to-trie-data-structure-and-algorithm-tutorials

- https://en.wikipedia.org/wiki/Trie

- https://www.youtube.com/watch?v=qA8l8TAMyig
