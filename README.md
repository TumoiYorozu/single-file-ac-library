
[ACL(ac-library)](https://atcoder.jp/posts/517) をマージしてシングルファイルで使えるようにしました．†邪悪†  
  
[marged_ACL.cpp](./marged_ACL.cpp) の内容に続けてコードを書けば，ACL をローカルの環境でも非AtCoderでもどこでも使えます．  

また，ACL のドキュメントを[ここからブラウザ上](https://tumoiyorozu.github.io/single-file-ac-library/document_ja/) で見れるようにしました．使い方はこっちを見てね．

## 例
[AtCoder Library Practice Contest  A - Disjoint Set Union](https://atcoder.jp/contests/practice2/tasks/practice2_a) を解いてみる例

```cpp
// ----------------------------------------------------------------
// marged_ACL.cpp の内容をここに貼る
// ----------------------------------------------------------------

#define rep(i,n) for(int i = 0; i < (n); ++i)
using namespace std;
using namespace atcoder;

int main(){
    int n,q;
    cin >> n >> q;

    dsu uf(n);

    rep(i, q){
        int t, u, v;
        cin >> t >> u >> v;
        if(t == 0){
            uf.merge(u, v);
        } else {
            cout << uf.same(u, v) << endl;
        }
    }
}
```
[コード例](https://atcoder.jp/contests/practice2/submissions/16566759)

## Visual Studio で使うときの Tips
[ツイート参照](https://twitter.com/TumoiYorozu/status/1303198376507269120)  
ACL (AtCoder Library) が Visual Studio でそのままでは使えなかったのでメモ  
  
【'_umul128': 識別子が見つかりませんでした 】  
→ x86(32bit) になってるので上の方のメニューから x64(64bit) に変更しましょう．  
  
【式は定数に評価されませんでした】  
→ internal_math.hpp の 86 行目 (is_prime_constexpr関数内)  
    for (long long a : {2, 7, 61}) {  
を  
    int v[] = { 2, 7, 61 };  
    for (long long a : v) {  
にする  


## 作られ方
以下のコードで [marged_ACL.cpp](./marged_ACL.cpp) は生成されました．

```bash
echo > tmp.cpp
cat atcoder/internal_bit.hpp          >> tmp.cpp
cat atcoder/internal_math.hpp         >> tmp.cpp
cat atcoder/internal_queue.hpp        >> tmp.cpp
cat atcoder/internal_scc.hpp          >> tmp.cpp
cat atcoder/internal_type_traits.hpp  >> tmp.cpp
cat atcoder/modint.hpp                >> tmp.cpp
cat atcoder/convolution.hpp           >> tmp.cpp
cat atcoder/dsu.hpp                   >> tmp.cpp
cat atcoder/fenwicktree.hpp           >> tmp.cpp
cat atcoder/lazysegtree.hpp           >> tmp.cpp
cat atcoder/math.hpp                  >> tmp.cpp
cat atcoder/maxflow.hpp               >> tmp.cpp
cat atcoder/mincostflow.hpp           >> tmp.cpp
cat atcoder/scc.hpp                   >> tmp.cpp
cat atcoder/segtree.hpp               >> tmp.cpp
cat atcoder/string.hpp                >> tmp.cpp
cat atcoder/twosat.hpp                >> tmp.cpp
cat tmp.cpp | sed '/<atcoder/d' |grep -v '^\s*$'  > marged_ACL.cpp
rm tmp.cpp
```


追記：コレで作ったほうがスマートだったな，次回があったらこっちで作ります
```bash
echo "#include<atcoder/all>" > tmp.cpp
python3 expander.py tmp.cpp
grep -v '^\s*$' combined.cpp > marged_ACL.cpp
rm tmp.cpp combined.cpp
```

# ひとこと
良ければ GitHub アカウント持ってる人は Star してください

