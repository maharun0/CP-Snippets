## Number Theory
### Prime Factorization

```
map<ll, int> factorize(ll n) {
    map<ll, int> m;
    
    for (int i = 2; i * i <= n; i++) {
        while (n % i == 0) {
            m[i]++, n /= i;
        }
    }
    if (n != 1) m[n]++;
        
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

### Big Integer Reminder / Large Division
- [Article](https://www.shawonruet.com/2016/07/big-integer-remainder.html)

```
ll bigIntRem(string& s, auto& m) {
    ll r = 0;
    
    bool isNeg = (s[0] == '-');
    for (ll i = isNeg; i < s.size(); i++)
        r = ((r * 10) + (s[i] - '0')) % m;
    
    if (isNeg) r = (-r + m) % m;
    
    return r;
}
```
