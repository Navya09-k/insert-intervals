import bisect
class Solution:
    def insert(self, intervals: list[list[int]], newInterval: list[int]) -> list[list[int]]:
        i = bisect.bisect_left(intervals, newInterval)
        merged = []   
        for iv in intervals[:i] + [newInterval] + intervals[i:]:
            if not merged or merged[-1][1] < iv[0]:
                merged.append(iv)
            else:
                merged[-1][1] = max(merged[-1][1], iv[1])
        return merged      
