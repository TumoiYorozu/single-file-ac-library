
[ACL(ac-library)](https://atcoder.jp/posts/517) をマージしてシングルファイルで使えるようにしました．†邪悪†  
  
[marged_ACL.cpp](./marged_ACL.cpp) の内容に続けてコードを書けば，ACL をローカルの環境でも非AtCoderでもどこでも使えます．  

また，ACL のドキュメントを[ここからブラウザ上](https://tumoiyorozu.github.io/single-file-ac-library/document_ja/) で見れるようにしました．使い方はこっちを見てね．

## 例
[AtCoder Library Practice Contest  A - Disjoint Set Union](https://atcoder.jp/contests/practice2/tasks/practice2_a) を解いてみる例

```
// ----------------------------------------------------------------
// marged_ACL.cpp の内容
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


## 作られ方
以下のコードで [marged_ACL.cpp](./marged_ACL.cpp) は生成されました．

```
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

