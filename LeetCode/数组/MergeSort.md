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
# 快速排序算法 

def QuickSort(nums,left,right):
    '''
    注意输入的参数，这里假设数组的边界
    left和right是闭合区间，即排序包含nums[left]和nums[right]
    '''
    #没有要排序的区间
    if left >= right:
        return
    
    l,r = left,right
    # 选一个哨兵，为了简单，选左边第一个元素
    # 在某些情况下，可能要随机去选
    pivot = nums[left]
    while l < r:
        # 从右边开始，寻找第一个小于哨兵的值
        while l < r and nums[r] >= pivot:
            r -= 1
        # 注意循环退出的条件
        # 要么 l < r 不满足，也就是一路退到最左边
        # 要么 nums[r] >= pivot 不满足，就是nums[r]小于pivot
        # 把这个值放在pivot的左边
        nums[l] = nums[r]
        # 从左边开始，寻找第一个大于哨兵的值
        while l < r and nums[l] <= pivot:
            l += 1
        # 注意循环退出的条件
        # 要么 l < r 不满足，也就是一路前进到最右边
        # 要么 nums[l] <= pivot 不满足，就是nums[l]大于pivot
        # 把这个值放在pivot的右边
        nums[r] = nums[l]
    # 注意循环退出的条件，一定是 l < r 不满足了，这个时候l==r
    # 把哨兵放在这个位置上
    nums[l] = pivot
    # 然后去排序哨兵左边的数组
    QuickSort(nums,left,l-1)
    # 然后去排序哨兵右边的数组
    QuickSort(nums,l+1，right)
