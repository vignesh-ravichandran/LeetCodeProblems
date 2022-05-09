You are given an array of k linked-lists lists, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.

 

Example 1:

Input: lists = [[1,4,5],[1,3,4],[2,6]]
Output: [1,1,2,3,4,4,5,6]
Explanation: The linked-lists are:
[
  1->4->5,
  1->3->4,
  2->6
]
merging them into one sorted list:
1->1->2->3->4->4->5->6
Example 2:

Input: lists = []
Output: []
Example 3:

Input: lists = [[]]
Output: []
 

Constraints:

k == lists.length
0 <= k <= 104
0 <= lists[i].length <= 500
-104 <= lists[i][j] <= 104
lists[i] is sorted in ascending order.
The sum of lists[i].length will not exceed 104.
Accepted
1,257,863
Submissions
2,670,019


Solution: 

        var mergeKLists = function(lists) {
            
            return merge(lists);
        };

        var merge  = function(lists){
            if(lists.length == 0 ) return null;
            let result = lists[0];
            
            if(lists.length < 2) return result;
            for(let i=1; i<lists.length; i++){
                result = mergeTwoList(result, lists[i]);
            }
            
            return result;
            
        }


        var mergeTwoList = function(list1, list2){
            if(list1 == null) return list2;
            if(list2 == null) return list1;
            
            let finalList = new ListNode(null);
            let headOffinalList = finalList;
            
            while(list1 != null && list2!= null){
                if(list1.val < list2.val){
                    finalList.next = list1;
                    list1 = list1.next;
                
                }else{
                    finalList.next = list2;
                    list2 = list2.next;
                }
                finalList = finalList.next;
            }
            while(list1 != null){
                finalList.next = list1;
                list1 = list1.next;
                finalList = finalList.next;
            }
            while(list2 != null){
                finalList.next = list2;
                list2 = list2.next;
                finalList = finalList.next;
            }
            
            return headOffinalList.next;
            
        }