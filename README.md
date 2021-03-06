# Competitive Coding Tricks

#### 1. Multiply a number by 2
```
    n = n << 1
```

#### 2. Divide a number by 2
```
    n = n >> 1
```

#### 3. Check if a number is odd or even
```
    n & 1 ? "ODD" : "EVEN"
```

#### 4. Maximum element of the array
```
    *max_element(a, a+n)
```

#### 5. Minimum element of the array
```
    *min_element(a, a+n)
```

#### 6. Sort elements of array in ascending order
```
    sort(a, a+n)
```

#### 7. Sort elements of array in descending order
```
    sort(a, a+n, greater<int>())
```

#### 8. Swap two numbers
```
    swap(a, b)
```
or you can use
```
    a ^= b;
    b ^= a;
    a ^= b;
```

#### 9. Test Case while loop
```
    ll t; cin>>t; while(t--){}
```

#### 10. GCD or HCF of two numbers
```
    __gcd(a, b)
```
or you can use
```
    ll gcd(ll a, ll b){return b ? gcd(b, a % b) : a;}
```
or you can use
```
    ll gcd(ll a,ll b){ll r; while(b){r = a % b; a = b; b = r;} return a;}
```

#### 11. Number of digits in a number
```
    floor(log10(n)) + 1
```

#### 12. Prime numbers less than n (Sieve of Eratosthenes)
```
    void SieveOfEratosthenes(int n){
        bool prime[n+1];
        memset(prime, true, sizeof(prime));
        for (int p = 2; p * p <= n; p++){
            if (prime[p] == true){
                for (int i = p * 2; i <= n; i += p)
                    prime[i] = false;
            }
        }
        for (int p = 2; p <= n; p++){
           if (prime[p]){
              cout << p << " ";
           }
        }
    }
```

#### 13. Prime Factors of a number
```
    void primeFactors(int n){
        while (n % 2 == 0){
            printf("%d ", 2);
            n = n / 2;
        }
        for (int i = 3; i <= sqrt(n); i = i + 2){
            while (n % i == 0){
                cout << i;
                n = n / i;
            }
        }
        if (n > 2){
            cout << n;
        }
    }
```
or you can use Sieve of Eratosthenes

#### 14. LCM of a number
```
    (a * b) / __gcd(a, b)
```

#### 15. Largest Sum Contiguous Subarray (Kadane's Algorith)
```
    int maxSubArraySum(int a[], int size){
        int max_so_far = INT_MIN, max_ending_here = 0;
        for (int i = 0; i < size; i++){
            max_ending_here = max_ending_here + a[i];
            if (max_so_far < max_ending_here){
                max_so_far = max_ending_here;
            }
            if (max_ending_here < 0){
                max_ending_here = 0;
            }
        }
        return max_so_far;
    }
```

#### 16. Check if a number is a power of two
```
    bool isPowerOfTwo(int n){
        return n && (!(n&(n-1)));
    }   
```

#### 17. Copy elements of one array to another
```
    copy_n(source, n, destination);
```

#### 18. Finding nth Root of a Number
```
    long double nthRoot(ll A, ll N)
    {
        // intially guessing a random number between
        // 0 and 9
        long double xPre = rand() % 10;

        //  smaller eps, denotes more accuracy
        long double eps = 1e-3;

        // initializing difference between two
        // roots by INT_MAX
        long double delX = INT_MAX;

        //  xK denotes current value of x
        long double xK;

        //  loop untill we reach desired accuracy
        while (delX > eps)
        {
            //  calculating current value from previous
            // value by newton's method
            xK = ((N - 1.0) * xPre +
                  (long double)A/pow(xPre, N-1)) / (long double)N;
            delX = abs(xK - xPre);
            xPre = xK;
        }

        return xK;
    }  
```

#### 19. Getting frequency of characters in a string
```
    void getFrequency(string strInput,map<char,int> & fMap)
    {
         map<char,int>::iterator it; //iterator to find the entries in map
         for(int i = 0 ; i < strInput.length() ; i++ )
         {
              char ch = strInput.at(i);
              it = fMap.find(ch); //find the character in the map
              if( it == fMap.end() ) //if not present in the map
              {
                    fMap.insert( make_pair(ch,1) );//add an entry
              }
              else
              {
                    it->second++; //else increment the frequency
              }
        }
    }
```
```
    void printFrequency(map<char,int> & fMap)
    {
         map<char,int>::iterator it;//iterator to loop through all the chars
         for( it = fMap.begin() ; it != fMap.end() ; ++it )
         {
            cout<<"["<< it->first<<"]"<<"->"<<it->second<<endl;
         }
    }   
```
