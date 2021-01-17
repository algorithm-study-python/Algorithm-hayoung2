## Trie 자료구조

- 트리 구조의 알고리즘(prefix tree). 
- 시간복잡도 O(m) -> 문자열에 특화됨, 문자열의 길이 만큼 검색 시간 소요. 
- 단점: 공간 복잡도, 다음 문자를 가리키는 노드가 계속해서 필요함(문자열 크기만큼), ![출처 : Wikipedia](https://upload.wikimedia.org/wikipedia/commons/thumb/b/be/Trie_example.svg/250px-Trie_example.svg.png)
- 각 노드에 key, value 값 을 가짐 key에는 하나의 알파벳 value는 그 key 다음에 해당하는 값

```python
# class Node 따로 만드는 것도 있음 
# words=["안녕하세요","안성탕면]
class Trie:
    # root에 글자 하나씩 넣음 
    # 끝날경우 endSymbol 이건 그냥 마지막으로 표시해서 넣은 듯.
    def __init__(self):
        self.root={}
        self.endSymbol="*"
    
    def add(self,word):
        # 노드 생성
        node=self.root
        # 한글자씩 넣음
        for letter in word:
            # node 안에 해당 글자 없을 경우
            if letter not in node:
                node[letter]={} # 새로 생성
            node=node[letter] # 글자 넣음 
        node[self.endSymbol]=word # 입력 모두 완료하고 끝 표시 
#{'안': {'녕': {'하': {'세': {'요': {'*': '안녕하세요'}}}}, '성': {'탕': {'면': {'*': '안성탕면'}}}}(출력)
```

