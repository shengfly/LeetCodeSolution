# 归并排序算法

```python
def Merge(left_nums,right_nums):
    ''' 目的： 把2个已经排序的数组 left_nums, right_nums
              合并到一个新的排好序的数组
    '''
    nums = [] # 新的数组，起始为空
    # 建立2个指针，分别指向2个数组
    left_index = 0 
    right_index = 0 
    while left_index < len(left_nums) and right_index < len(right_nums):    
        # 比较2个数组队头的元素，谁小谁先进 （从小到大排序）
        if left_nums[left_index] < right_nums[right_index]:
            nums.append(left_nums[left_index])
            left_index += 1
        else:
            nums.append(right_nums[right_index])
            right_index += 1
    # 注意循环结束的条件，至少有一个数组到头了。那么另外一个数组有可能还有剩下的元素，需要处理
    # 如果 是 right_index < len(right_nums) 不满足了，说明左边数组有剩余元素
    while left_index < len(left_nums):
        nums.append(left_nums[left_index])
            left_index += 1
    # 如果 是 left_index < len(left_nums) 不满足了，说明右边数组有剩余元素
    while right_index < len(right_nums):
        nums.append(right_nums[right_index])
            right_index += 1
    return nums

def MergeSort(nums):
    # 如果数组只有1个元素，小事化了。 不需要排序了，（已经排好序），直接返回
    if len(nums) <= 1:
        return nums
    #否则，继续大事化小
    mid = len(nums)//2
    # 注意，这里是递归调用，先去排左边，然后去排右边，最后将2个数组合并
    left = MergeSort(nums[:mid])
    right = MergeSort(nums[mid:])
    # 将已经排好序的left、right合并，调用前面的合并算法
    return Merge(left,right)
```
