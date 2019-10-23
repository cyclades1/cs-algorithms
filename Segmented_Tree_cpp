#include<bits/stdc++.h>
using namespace std;

#define intmax 5000000
#define endl "\n"
#define add(a,b) a+b

typedef long long ll ;

ll tree[intmax];
ll a[intmax];

void build(ll node , ll start , ll end, ll a[])
{
    if( start == end)
    {
        tree[node]=a[start];
    }
    else
    {
        ll mid = (start + end)/2;
        build(2*node, start, mid,a);
        build (2*node+1 , mid+1, end,a);
        tree[node]= add(tree[2*node], tree[2*node+1]);
    }
}

void update(ll node , ll start , ll end, ll id, ll value)
{
    if(start == end)
    {
        tree[node]+= value;
    }
    else
    {
        ll mid = (start + end)/2;
        if(id<= mid && id >= start)
        {
            update(2*node , start ,mid , id, value);
        }
        else if(id<=end && id >mid)
        {
            update(2*node +1, mid + 1, end , id , value);
        }
        tree[node]= add( tree[2*node], tree[2*node +1]);
    }
}

ll query (ll node , ll start, ll end , ll l, ll r)
{
    if(r<start || l> end)
    {
        return 0;
    }
    if(l<= start && end <= r)
    {
        return tree[node];
    }
    ll mid = (start+end)/2;
    ll p1 = query(2*node, start ,mid , l, r);
    ll p2 = query(2*node +1, mid +1 , end, l , r);
    return (add(p1,p2));
}

int main()
{
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);
    ll t;
    cin >> t;

    while(t--){
    ll n , q;
    cin >> n>> q;
    for(ll i =1 ;i<=n; i++)
        a[i]=0;
    build(1, 1, n,a);
    while(q--)
    {
        int ch ;
        cin >> ch;
        if(ch == 1)
        {
            ll l ,r;
            cin >> l >>r;
            cout<<query(1,1,n,l,r)<<endl;
        }
        else
        {
            ll l  , r, value;
            cin >> l>>r>>value;
            for(ll i = l;i<=r;i++)
            {
                a[i]=value;
                update(1,1,n,i,value);
            }
        }
    }
    }
    return 0;
}
