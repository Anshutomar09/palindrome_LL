# palindrome_LL
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        ListNode* slow=head;
        ListNode*fast=head;
        while(fast!=NULL and fast->next!=NULL)//find mid
        {
            slow=slow->next;
            fast=fast->next->next;
            
        }//slow=mid
        if(fast!=NULL and fast->next!=NULL)
            slow=slow->next;
        ListNode* prev=NULL;
        while(slow!=NULL and slow->next!=NULL)//reverse
        {
            ListNode*temp=slow->next;
            slow->next=prev;
            prev=slow;
            slow=temp;   
        }
        if(slow!=NULL){    
        slow->next=prev;
        }
        
        fast=head;
        while(slow and fast){//comparing
            if(slow->val!=fast->val){
                return false;
            }
            slow=slow->next;
            fast=fast->next;
            
        }
        return true;
    }
};
