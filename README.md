# Kth-Smallest-Instructions
Bob is standing at cell (0, 0), and he wants to reach destination: (row, column). He can only travel right and down. You are going to help Bob by providing instructions for him to reach destination.  The instructions are represented as a string, where each character is either:  'H', meaning move horizontally , or 'V', meaning move vertically.

class Solution:
   def kthSmallestPath(self, destination: List[int], k: int) -> str:
        from math import comb
        r, c = destination
        
        ret = []
        remDown = r
        for i in range(r + c):
            remSteps = r + c - (i + 1)
            com = comb(remSteps, remDown)
            if com >= k:
                ret.append("H")
            else:
                remDown -= 1
                k -= com
                ret.append("V")
                
        return ''.join(ret)
        
