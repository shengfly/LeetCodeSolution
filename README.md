# LeetCode拍案惊奇

80. 指针分离思路-妙解

    题目：给定一个排列好的数组，删除2个以上的相同元素
        
        同题目26相似，要求删除所有相同的元素。双指针法。
        
        题目26可以用双指针法来搞定。慢指针指向保留数组的最后一个位置，快指针则快速向前搜索，只要碰到与慢指针指向不相同的元素，就进行copy。
        
        默认： check的位置就是慢指针的位置
        
        拍案惊奇： 而题目80则要求最多2个相同的元素，简单的做法就是慢指针的位置与check的位置并不重合，check指针的位置统一向后移动2个位置，就搞定此算法。
        
        慢指针的位置和check的位置非常讲究。

169, 减不完-求大于多半个元素

   题目： 求一个数组中大于一半的元素

    遇到相同就加，不同就减，遇0换元素，最后剩下的就是那个最多的。最多的就是减不完

189, 翻转再翻转-妙解数组旋转问题

   题目：旋转一维数组k位

    先翻转整个数组，再翻转局部数组

55,45, 指针辐射距离

  题目：判断是否能跳跃到结尾

        用一个指针指向每次跳跃所能达到的最远距离，然后不停地更新这个指针，看是否能跳出数组
