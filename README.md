def exists(self,val):
    if val==self.val:
        return True

    if val<self.val:
        if self.left==None:
            return False
        return self.left.exists(val)

    if self.right==None:
        return False
    return self.right.exists(val)

#binary search tree operations in python

#create a node
class Node:
    def __init__(self,key):
        self.key=key
        self.left=None
        self.right=None

#Preorder traversal
def preOrder(root):
    if root is not None:
        #traversal root
        print(str(root.key)+"->",end='')

        #traversal left
        preOrder(root.left)

        #traversal right
        preOrder(root.right)

#Inorder traversal
def inOrder(root):
    if root is not None:
            
        #traversal left
        inOrder(root.left)

        #traversal root
        print(str(root.key)+"->",end='')

        #traversal right
        inOrder(root.right)

#Postorder traversal
def postOrder(root):
    if root is not None:
            
        #traversal left
        postOrder(root.left)

        #traversal right
        postOrder(root.right)

        #traversal root
        print(str(root.key)+"->",end='')

#insert a node
def insert(node,key):

#return a new node if the tree is empty
    if node is None:
        return Node(key)

    #traverse to the right place and insert the node
    if key<node.key:
        node.left=insert(node.left,key)
    else:
        node.right=insert(node.right,key)
    return node

def exists(node,val):
    if val==node.key:
        return True

    if val< node.key:
        if node.left==None:
            return False
        return exists(node.left,val)

    if node.right==None:
        return False
    return exists(node.right,val)

#find the inorder successor
def minValueNode(node):
    current=current.left

    #find the leftmost leaf
    while(current.left is not None):
        current=current.left

    return current

#deleting a node
def deleteNode(root,key):

    #return if the tree is empty
    if root is None:
        return root

    #find the node to be deleted
    if key<root.key:
        root.left=deleteNode(root.left,key)
    elif(key>root.key):
        root.right=deleteNode(root.right,key)
    else:
        #if the node is with only one child or no child
        if root.left is None:
            temp=root.right
            root=None
            return temp

        elif root.right is None:
            temp=root.left
            root=None
            return temp

        #if yhe node has two children, place the inorder succesor in 
        #position of the node to be deleted
        temp=minValueNode(root.right)

        root.key=temp.key

        #deleting the inorder successor
        root.right=deleteNode(root.right,temp.key)

    return root

root=None
root=insert(root,12)
root=insert(root,6)
root=insert(root,0)
root=insert(root,5)
root=insert(root,16)
root=insert(root,7)
root=insert(root,90)
root=insert(root,21)
root=insert(root,3)
root=insert(root,4)

print("\n")
print("\n Preorder traversal =",end='')
preOrder(root)

print("\n")
print("\n Inorder traversal =",end='')
inOrder(root)

print("\n")
print("\n Postorder traversal =",end='')
postOrder(root)

print("\n")
x=int(input("enter which node you want to search ="))
if (exists(root,x)):
    print("Found")
else:
    print("Not found")
print("\nDelete 3")
root=deleteNode(root,3)
print("Inorder traversal =",end='')
inOrder(root)



    
    


        
            

    


    

