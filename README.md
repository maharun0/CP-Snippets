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

```
auto mod(auto& x, auto& y) {
    return x >= 0? (x % y) : (((x % y) + y) % y);
}
```
