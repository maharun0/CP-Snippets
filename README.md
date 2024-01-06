## Number Theory
### Prime Factorization

```
map<ll, int> factorize(ll n) {
    map<ll, int> m;
    
    for (int i = 2; i * i <= n; i++) {
        while (n % i == 0) {
            m[i]++;
            n /= i;
        }
    }
    
    if (n != 1)
        m[n]++;
        
    return m;
}
```

### Calculate Mod
x % y = **x** - ('**biggest multiple of y**' which is 'less than x')

```
auto mod(auto& x, auto& y) {
    return x >= 0? (x % y) : (((x % y) + y) % y);
}
```

### Binary Exponentiation

```
// n^p
long long binExpo(int n, int p) {
    long long res = 1;
    while (p > 0) {
        if (p & 1) res *= n;
        n *= n;
        p >>= 1;
    }
    return res;
}
```

### Big Mod

```
// n^p % m
int bigMod(int n, int p, int m) {
    n %= m;
    int res = 1;
    while (p > 0) {
        if (p & 1) res = n * res % m;
        n = n * n % m;
        p >>= 1;
    }
    return res;
}
```

### Big Integer Reminder / Long Division

```
ll bigIntRem(string num, ll m) {
    ll res = 0;
    
    bool isNeg = (num[0] == '-');
    for (ll i = isNeg; i < num.size(); i++) {
        int d = num[i] - '0';
        res = (res * 10) + d;
        res %= m;
    }
    
    if (isNeg) res = (-res + m) % m;
    
    return res;
}
```
