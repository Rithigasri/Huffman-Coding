# EXPERIMENT 12: HUFFMAN CODING
## AIM:
To implement Huffman coding to compress the data using Python.

## SOFTWARE REQUIRED:
1. Anaconda - Python 3.7

## ALGORITHM
### Step 1:
Declare the string.
### Step 2:
Declare a class for creating nodes.
### Step 3:
Define a function to implement huffman coding.
### Step 4:
calculate the frequency for the gicen string.
### Step 5:
Display the huffman coding as output.

## PROGRAM:

``` 
# Get the input String:
string="Rithiga Sri B 212221230083"

#Creating tree nodes:
class NodeTree(object):
    def __init__(self,left=None,right=None):
        self.left=left
        self.right=right
    def children(self):
        return (self.left,self.right)

# Main function to implement huffman coding:
def huffman_code_tree(node,left=True,binString=''):
    if type(node) is str:
        return {node:binString}
    (l,r)=node.children()
    d=dict()
    d.update(huffman_code_tree(l,True,binString+'0'))
    d.update(huffman_code_tree(r,False,binString+'1'))
    return d

# Calculate frequency of occurrence:
freq={}
for c in string:
    if c in freq:
        freq[c]+=1
    else:
        freq[c]=1
freq=sorted(freq.items(),key=lambda x:x[1],reverse=True)
nodes=freq

# Print the characters and its huffmancode
while len(nodes)>1:
    (key1,c1)=nodes[-1]
    (key2,c2)=nodes[-2]
    nodes=nodes[:-2]
    node=NodeTree(key1,key2)
    nodes.append((node,c1+c2))
    nodes=sorted(nodes,key=lambda x:x[1],reverse=True)
    
huffmanCode=huffman_code_tree(nodes[0][0])
print('Char | Huffman Code')
print('----------------------')
for(char,frequency) in freq:
    print('%-4r |%12s' % (char,huffmanCode[char]))
```
## OUTPUT:

### Print the characters and its huffmancode:
![image](https://github.com/Rithigasri/Huffman-Coding/assets/93427256/31c4e385-be48-4cad-a6f4-59e619056485)

## RESULT:
Thus the huffman coding was implemented to compress the data using python programming.
