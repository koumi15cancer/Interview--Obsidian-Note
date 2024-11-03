A trie (also known as a Prefix Tree) stores a set of strings in a tree-like data structure. The trie below stores the strings APPLE, APP, BAT, BALL, BATS, and BALL:
![[Screenshot 2024-11-03 at 11.42.44 PM.png]]

Strings with a common prefix share the same nodes in the trie. For example, the strings APPLE and APP share the nodes A, P, and P.

A trie is commonly used to implement features like spell checkers and auto-complete. For example, if we type in the string "BA", then our trie can suggest "BALL" and "BAT" as possible completions.

### Basics

- A trie consists of a series of nodes arranged in a tree. Each node in the trie represents a character in one of the strings in the trie, and its children represent the next character in the string.
    
- Each node also has a boolean value that indicates whether the node represents the end of a word. Nodes where this boolean value is true are colored blue in this guide.
    
- A trie supports 3 main operations: _search(word)_, _insert(word)_, and _delete(word)_.

#### Trie Class

A trie is typically implemented as a class with a reference to root of the trie of type TrieNode. The class has methods to search, insert, and delete words from the trie.

```python
class Trie:

    def __init__(self):

        self.root = TrieNode()

    def search(self, word):

        # return True if word is in trie, False otherwise

        pass

    def insert(self, word):

        # insert word into trie

        pass

    def delete(self, word):

        # delete word from trie

        pass

```

#### TrieNodes

The TrieNode class can be defined as:
```python
class TrieNode:

    def __init__(self, children = {}, eow = False):

        self.children = children

        self.is_end_of_word = eow


```

## Trie Operations

### Search

The search operation takes a search term as input and returns whether the term exists in the trie.

We start from the root node and the first character of the search term. We then traverse down the trie by checking if any of the children of the current node match the next character in the search term. If they do, we move to that node and continue the search with the next character in the search term.


#### Time Complexity

O(L), where L is the length of the word being searched in the worst case we need to traverse L nodes in the Trie to find the word. Each node traversal takes constant time O(1), for a total of O(L) operations.

### Insertion

The insert operation takes a word as input and adds it to the trie.

We traverse the trie until we reach the last character of the search term. From there, we add the nodes that don't exist already in the trie, and mark the last node as the end of a word.

#### Time Complexity

O(L) where L is the length of the word being inserted. In the worst case, such as when the trie is empty or the word being inserted has no common prefixes with existing words, we need to insert L nodes, each of which takes constant time O(1)

### Deletion

The delete operation deletes a word from the trie.

We traverse down to the last character of the word we want to delete, set the "end of word" flag to false, and then remove any nodes that are not part of any other words in the trie.

#### Time Complexity

O(L). In the worst case, such as when the word to delete is the only word in the trie, we need to first traverse L nodes in the trie to find the word to delete, and then delete L nodes. Each node traversal takes constant time O(1), for a total 2L operations, which is O(L).

### Summary

|Operation|Description|Time Complexity|
|---|---|---|
|Search|Search for a word in the trie|O(L)|
|Insert|Insert a word in the trie|O(L)|
|Delete|Delete a word from the trie|O(L)|

### Space Complexity

The space complexity of a trie is O(C), where C is the total number of characters between all the words stored in the trie. This is due to the worst case, which happens when there are no common prefixes between the words stored in the trie.
