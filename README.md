Lexicographic rank of a String
#User function Template for python3
class Solution:
def f(self,n):
if(n&lt;=1):
return 1
return n*self.f(n-1)
def countr(self,S,i):
c=0
for j in range(i+1,len(S)):
if(S[i]&gt;S[j]):
c+=1
return c

def findRank(self, S):
sum=1
mul=self.f(len(S))
for i in range(len(S)):
mul=mul//(len(S)-i)
sum += self.countr(S,i)*(mul)
return sum

143. Reorder List
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reorderList(self, head: Optional[ListNode]) -&gt; None:
        &quot;&quot;&quot;
        Do not return anything, modify head in-place instead.
        &quot;&quot;&quot;
        slow,fast=head,head
        while(fast.next and fast.next.next):
            slow=slow.next
            fast=fast.next.next
       
        prev=None
        curr=slow.next  #taking 2nd half ist element
        slow.next=None  #breaking two halfs

        while curr:
            nextt=curr.next #remembering
            curr.next=prev
            prev=curr
            curr=nextt
       
        head1,head2=head,prev
        while head2:
            temp1=head1.next
            temp2 = head2.next
            head1.next=head2
            head2.next=temp1
            head1,head2=temp1,temp2
             
       
        44. Wildcard Matching
class Solution:
    def isMatch(self, st: str, pattern: str) -&gt; bool:
        i,j,mat,star=0,0,0,-1
        while(i&lt;len(st)):
            if(j&lt;len(pattern) and (st[i]==pattern[j] or pattern[j]==&#39;?&#39;) ):
                i+=1
                j+=1
            elif(j&lt;len(pattern) and pattern[j]==&#39;*&#39;):
                star=j
                mat=i
                j+=1
            elif(star!=-1):
                j=star+1
                mat+=1
                i=mat
            else:
                return False
        while(len(pattern)&gt;j and pattern[j]==&#39;*&#39;):
            j+=1
        return j==len(pattern)

Maximum subset sum
from typing import List
class Solution:
def findMaxSubsetSum(self, N : int, A : List[int]) -&gt; int:
# code here
if(N==1):
return A[0]
prv1=0
prv2=A[0]
for i in range(1,len(A)):

cur=max(prv2,prv1) +A[i]
cur2=prv2
prv2, prv1= cur,cur2
return max(prv1,prv2)
53. Maximum Subarray
class Solution:
    def maxSubArray(self, nums: List[int]) -&gt; int:
       
        m=float(&#39;-inf&#39;)
        sum=0
        for i in range(len(nums)):
            sum+=nums[i]
            if(sum&gt;m):
                m=sum
            if(sum&lt;0):
                sum=0
        return m

           
        return m

168. Excel Sheet Column Title
class Solution:
    def convertToTitle(self, columnNumber: int) -&gt; str:
        s=&quot;&quot;
        while(columnNumber&gt;0):
            columnNumber=columnNumber-1
            s=chr(columnNumber%26+ord(&#39;A&#39;))+s
            columnNumber//=26
        return s
       
179. Largest Number
class Solution:
    def largestNumber(self, nums: List[int]) -&gt; str:
        l=[]
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                # print(str(nums[i])+str(nums[j]))
                if((str(nums[i])+str(nums[j]))&gt;(str(nums[j])+str(nums[i]))):
                    continue
                    # print(nums)
                else:
                    nums[j],nums[i]=nums[i],nums[j]
                    # print(nums)

        return &#39;&#39;.join(map(str, nums)).lstrip(&#39;0&#39;) or &#39;0&#39;

168. Excel Sheet Column Title
class Solution:
    def convertToTitle(self, columnNumber: int) -&gt; str:
        s=&quot;&quot;
        while(columnNumber&gt;0):
            columnNumber=columnNumber-1
            s=chr(columnNumber%26+ord(&#39;A&#39;))+s
            columnNumber//=26
        return s
       
867. Transpose Matrix
class Solution:
    def transpose(self, matrix: List[List[int]]) -&gt; List[List[int]]:
        row=len(matrix)
        col=len(matrix[0])
        res=[[0]*row for _ in range(col)]
        for i in range(row):
            for j in range(col):
                res[j][i]=matrix[i][j]
        return res

Cocubes-Coding-18
import sys
tokens = sys.stdin.read().strip().split()
if not tokens:
sys.exit()
for tok in tokens:
n = int(tok)
if n &lt;= 0:
print(0)

continue
s = 0
m = n
while m &gt; 0:
s += m % 10
m //= 10
print(n // s if n % s == 0 else 0)
Maximum element and its index
n=int(input())
l=list(map(int,input().split()))
m=0
# print(l[0])
for i in range(n):
if(l[i]&gt;m):
m=l[i]
s=i
print(m)
print(s)

Program to Count numbers on fingers
def count_num_finger( n ):
r = n % 8
if r == 0:
return 2
if r &lt; 5:
return r
else:
return 10 - r
# Driver Code
n = 30
print(count_num_finger(n))

GCD of two numbers
class Solution:
def gcd(self, a, b):
# code here
if(b==0):
return a
return self.gcd(b,a%b)

Even numbers at even index and odd numbers at odd index

#User function Template for python3
class Solution:
def reArrange(self, arr, N):
# code here
oi=1
ei=0
while(oi&lt;N and ei&lt;N):
if(arr[oi]%2==1):
oi+=2
elif(arr[ei]%2==0):
ei+=2
else:
arr[oi],arr[ei]=arr[ei],arr[oi]
oi+=2
ei+=2

231. Power of Two
class Solution:
    def isPowerOfTwo(self, n: int) -&gt; bool:
       
        t=1
        while(n&gt;=t):
            if(n==t):
                return True
            t=t&lt;&lt;1
           
        return False
