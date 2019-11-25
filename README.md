# _*_  coding : utf8  _*_
import os
import re
from collections import namedtuple
from sys import stdout
class Node():
    #节点类
    def __init__(self,data=-1):
        self.data=data
        self.left = None
        self.right = None
class Tree():
    #树类
    def __init__(self):
        self.root = Node()
    def add(self,data):
        #为树加入节点
        node = Node()
        node.data = data
        #node = Node(data)# 我在此处中有疑问，可以直接将类当成函数吗
        if self.root.data == -1:#如果树为空，则对树节点赋值
            self.root =node
        else:
            myque = []
            treenode = self.root
            myque.append(treenode)
            while myque:
                treenode = myque.pop(0)
                if treenode.left is None:
                    treenode.left = node
                    print("treenode.left.data:",treenode.left.data)
                    return
                elif treenode.right is None:
                    treenode.right = node
                    print("treenode.right.data:", treenode.right.data)
                    return
                else:
                    myque.append(treenode.left)
                    myque.append(treenode.right)
    # 前序遍历二叉树(NLR)
    def preorder(self,root):
        if root is None:
            return
        node_joint = []
        node_joint.append(root)
        while node_joint:
            node=node_joint.pop(0)
            print(node.data)
            if node.left is not None:
                node_joint.append(node.left)
            if node.right is not None:
                node_joint.append(node.right)
    def preoder(self,root):
        tree = Tree()
        if root is not None:
            print(root.data)
            tree.preoder(root.left)
            tree.preoder(root.right)
    #z中序遍历二叉树(LNR)
    def inorder(self,root):
        tree = Tree()
        #tree.root = root
        if root is not None:
            tree.inorder(root.left)
            print(root.data)
            tree.inorder(root.right)
    #后序遍历二叉树（LRN）
    def postorder(self,root):
        tree = Tree()
        if root is not None:
            tree.postorder(root.left)
            tree.postorder(root.right)
            print(root.data)
    #层序遍历二叉树
    def levelorder(self,root):
        if root is None:
            return
        queue = []
        queue.append(root)
        while queue:
            now_node =queue.pop(0)
            print(now_node.data)
            if now_node.left is not None:
                queue.append(now_node.left)
            if now_node.right is not None:
                queue.append(now_node.right)

if __name__ == "__main__":
    datas = [1,2,3,4,5,6,7,8,9]
    tree = Tree()
    for data in datas:
        tree.add(data)
    print("###################二叉树层级遍历：")
    tree.postorder(tree.root)
