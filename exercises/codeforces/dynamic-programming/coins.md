# Coins

```
// https://codeforces.com/gym/101102/problem/A
#include<bits/stdc++.h>
using namespace std;

typedef long long int ll;

const int N =15000;
const int mod=1e9+7;
const int cold = 200;
const int rowd = 16000;
int a[cold],b[cold];
ll dp[cold][rowd],nyan[cold][rowd];
ll ans;

int i, j;
int T,n,m,k,w;
int main() {    
    scanf("%d",&T);
    while(T--){
        memset(dp,0,sizeof(dp));
        memset(nyan,0,sizeof(nyan));
        scanf("%d%d%d%d",&n,&m,&k,&w);
        for(i=0; i<n; i++)
            scanf("%d",&a[i]);
        
        for(i=0; i<m; i++)
            scanf("%d",&b[i]);
        
        dp[0][a[0]]=1;
        dp[0][0]=1;
        
        for(i=1;i<n;i++){
            for(j=0;j<=N;j++){
                dp[i][j]+=dp[i-1][j];
                if(j-a[i]>=0) dp[i][j]=(dp[i][j]+dp[i-1][j-a[i]])%mod;
            }
        }
        
        nyan[0][b[0]]=1;
        nyan[0][0]=1;
        
        for(i=1; i<m; i++){
            for(j=0; j<=N; j++){
                nyan[i][j]+=nyan[i-1][j];
                if(j-b[i]>=0) nyan[i][j]=(nyan[i][j]+nyan[i-1][j-b[i]])%mod;
            }
        }
        
        ans=0;
        
        for(i=0; i<=w; i++)
            if(abs(w-i-i)<=k) ans=(ans+dp[n-1][i]*nyan[m-1][w-i])%mod;
        
        printf("%I64d\n",ans);
    }
    return 0;
}

```
