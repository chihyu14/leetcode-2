# Some thought about algorithm

## How to analyze problemom
### Understand the problem
### Basic methods
* Split the problem to smaller problem
  Split it to smaller problem. But how to split is also a problem. 
  
  e.g. Palindrome Palindrome II.

## How to make programe faster?
### Record
Record values that need computed many times. It could change the complexity of the algorithm. If not using record, it will exceed time limit.

e.g. Palindrome Palindrome II; Distinct Subsequences; Edit Distance.

### Hash
Hash is very very helpful. It could save much time.

e.g. Two Sum; Longest Consecutive Sequence.

# Specific problems

## Palindrome Partitioning II
Write programe more effectively. It *matters*.

e.g.

    for(size_t i = 0; i < need_cut.size(); i ++){
        if(isPalindrome(s, need_cut[i], len - 1)){
            return n; 
        }
        size_t start = need_cut[i];
        for(size_t j = start; j < len - 1; j ++){
            if(record[j + 1] != 0 && isPalindrome(s, start, j)){
                tmp.push_back(j + 1);
                record[j + 1] = 0;
            }
        }
    }
    
=>

    for(size_t i = 0; i < need_cut.size(); i ++){
        if(isPalindrome(s, need_cut[i], len - 1)){
            return n; 
        }
    }

    for(size_t i = 0; i < need_cut.size(); i ++){
        size_t start = need_cut[i];
        for(size_t j = start; j < len - 1; j ++){
            if(record[j + 1] != 0 && isPalindrome(s, start, j)){
                tmp.push_back(j + 1);
                record[j + 1] = 0;
            }
        }
    }
    
## Longest Consecutive Sequence
I usually use bit map to solve the problem. And I have already recognized the solution will be very inefficient when the range of the element in the array is very large, e.g. {-200000, 200000}. Today I think I could use map to solve it suddenly. Finally I solve the problem. What a big surprise!