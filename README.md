# Assignment-01-2Sum-and-Complexity
The difference between Brut force vs. Hash

#include <iostream>
#include <vector>
#include <unordered_map>

using namespace std;

//info:
//integer vector nums
//integer target 
//return indices of 2 dif elements whose value add to target= (i,j) 

//BrutForce
//const = for the function to not chnage the vectors content
//int target = local copy of integer
vector<int> twoSumBruteForce(const vector<int> & nums, int target)
{
    //for(first index; continue looping while is less tha n ; increment i for each iteration)
    for(int i = 0; i < nums.size(); ++i)
    {
        // J= i+ 1 (distinct pairs, one position ahead of i)
        for(int j = i + 1; j < nums.size(); ++j)
        {
            //then if target is 2
            //if 1 + 1 = 2 the return 1 and 1
            if(nums[i] + nums[j] == target)
            {
                return{i,j};
            }
        }
    }
    //hands back an empty vector 
    return{};
}

//Hash
//vector<int> = vector of ints that we are going to read 
//const vector<int> & nums= can't change it just reads it.
vector<int> twoSumHash(const vector<int> & nums, int target)
{
    //unordered map we use it for constant lookups in hasH(TO LOOK QUICKLY)
    //map is for binary search
	unordered_map<int,int> index;
	
	 for(int i = 0; i < nums.size(); ++i)
	  {
      //what do i need
	   int needed = target - nums[i];

      //it searches where the needed int is in the vector
      //nums = {2, 7, 11, 15}, target = 9
      //i= 1, nums[i]= 7, needed = 2, Yes, return {0,1}
	   if(index.count(needed))
	   {
       		//i saw it here, then it returns both indices
		   return {index[needed], i};
	   }
     
       //if not then it still remebers this number
	   index[nums[i]] = i;
	 }
	 return {};
	
}

//To not have it repeat in int main()
void print(const string& name, const vector<int>& nums, const vector<int>& answer)
{
		//In case its empty it prints not valid
    if(answer.empty())
    {
        cout << name << ": not valid"  << endl;
        return;
    }
    cout << name << ": [" <<answer[0]<< ", "<<answer[1]
    << "] --> " << nums[answer[0]] << " + " << nums[answer[1]]
    <<" = " << nums[answer[0]] + nums[answer[1]] << endl;

}

int main()
{
		//separate them in braces to be able to reuse the variables
    {
     //Test 
    vector<int> nums = {15, 4, 18, 8, 19, 22, 24, 59, 59, 20, 18, 12, 36, 42, 9}; 
    int target = 24;
    print("Test 1 BrutForce", nums, twoSumBruteForce(nums,target));
    print("Test 1 Hash", nums, twoSumHash(nums,target));
        
    }

    {
     //Test 1
    vector<int> nums = {2,10,26,15,10,2,1,0}; 
    int target = 40;
    print("Test 2 BrutForce", nums, twoSumBruteForce(nums,target));
    print("Test 2 Hash", nums, twoSumHash(nums,target));
        
    }

    {
     //Test 2 duplicate
    vector<int> nums = {3,2,3,15,10,2,1,5,5}; 
    int target = 6;
    print("Test 3 BrutForce", nums, twoSumBruteForce(nums,target));
    print("Test 3 Hash", nums, twoSumHash(nums,target));
        
    }

    {
     //Test 3 negatives
    vector<int> nums = {-2,10,-26,15,-10,2-1,0,-5, 18, 8, 19, -22, 2}; 
    int target = -15;
    print("Test 4 BrutForce", nums, twoSumBruteForce(nums,target));
    print("Test 4 Hash", nums, twoSumHash(nums,target));
        
    }

    {
     //Test 4 big numbers
    vector<int> nums = {2000,1500,5000,4000}; 
    int target = 6000;
    print("Test 5 BrutForce", nums, twoSumBruteForce(nums,target));
    print("Test 5 Hash", nums, twoSumHash(nums,target));
        
    }
    
     return 0;          
}
