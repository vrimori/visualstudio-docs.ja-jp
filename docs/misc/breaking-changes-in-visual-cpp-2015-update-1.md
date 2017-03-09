---
title: "Visual C++ 2015 Update 1 での互換性に影響する変更点 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c0b1c2b-e1cf-4767-885b-b98df9b3730e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "mithom"
manager: "ghogen"
---
# Visual C++ 2015 Update 1 での互換性に影響する変更点
Visual C\+\+ 2015 Update 1 にアップグレードすると、以前に正常にコンパイルと実行ができたコードでコンパイル エラーやランタイム エラーが発生する場合があります。 コンパイラとランタイムの動作でこのような問題を引き起こす変更は*互換性に影響する変更*と呼ばれ、通常は C\+\+ 言語標準、関数シグネチャ、メモリ内のオブジェクトのレイアウトの変更によって必要となります。  
  
 ここからは、Visual C\+\+ 2015 Update 1 の特定の互換性に影響する変更点について説明します。この記事における「新しい動作」または「現在」という語は、そのバージョンを指します。 「従来の動作」や「以前」という語は、Visual Studio 2015 以前のリリースにおける初期リリースを指します。 Visual Studio 2013 と Visual Studio 2015 の間で発生した互換性に影響する変更点については、「[Visual C\+\+ 2015 での互換性に影響する変更点](/visual-cpp/porting/visual-cpp-change-history-2003-20151)」をご覧ください。  
  
-   [コンパイラの互換性に影響する変更点](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Visual C\+\+ コンパイラ  
  
-   **プライベートの仮想基底クラスと間接継承**  
  
     以前のバージョンのコンパイラでは、派生クラスは*間接的に派生した*`private virtual`基本クラスのメンバー関数を呼び出すことができました。 この従来の動作は正しい動作ではなく、C\+\+ 標準に準拠していません。 コンパイラはこの方法で記述されたコードを受け入れなくなりました。その結果、コンパイラ エラー C2280 を発行します。  
  
 **エラー C2280: *'void \* S3::\_\_delDtor\(unsigned int\)'*: 削除された関数を参照しようとしています**     例 \(変更前\)  
  
    ```cpp  
    class base { protected: base(); ~base(); }; class middle: private virtual base {};class top: public virtual middle {}; void destroy(top *p) { delete p;  // }  
    ```  
  
     例 \(変更後\)  
  
    ```cpp  
    class base;  // as above class middle: protected virtual base {}; class top: public virtual middle {}; void destroy(top *p) { delete p; }  
    ```  
  
     または  
  
    ```  
    class base;  // as above class middle: private virtual base {}; class top: public virtual middle, private virtual bottom {}; void destroy(top *p) { delete p; }  
    ```  
  
-   **オーバーロードされた operator new と operator delete**  
  
     以前のバージョンのコンパイラでは、メンバー以外の`operator new` とメンバー以外の`operator delete` を static として宣言することや、グローバル名前空間以外の名前空間で宣言することが許可されていました。  この従来の動作のせいで、プログラマが意図した `new` または `delete` 演算子の実装がプログラムによって呼び出されないという危険性が生じ、結果として、問題のあるランタイム動作が警告なしに生じていました。 コンパイラはこの方法で記述されたコードを受け入れなくなりました。代わりにコンパイラ エラー C2323 を発行します。  
  
 **エラー C2323: *'operator new'*: メンバー以外の operator new または delete 関数が static として宣言されていない、またはグローバル名前空間以外の名前空間で宣言されていない可能性があります。**     例 \(変更前\)  
  
    ```cpp  
  
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323  
    ```  
  
     例 \(変更後\)  
  
    ```cpp  
  
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'  
    ```  
  
     また、コンパイラは特定の診断を行いませんが、インラインの operator new の形式は不適切であると見なされます。  
  
-   **非クラス型で 'operator *type*\(\)' \(ユーザー定義の変換\) を呼び出す**  
  
     以前のバージョンのコンパイラでは 'operator *type*\(\)' を非クラス型で呼び出すことが許可されていましたが、それは何の警告もなく無視されていました。 この従来の動作のせいで、問題のあるコードが警告なしに生成される危険性が生じ、結果として、予期しないランタイム動作の原因となっていました。 コンパイラはこの方法で記述されたコードを受け入れなくなりました。代わりにコンパイラ エラー C2228 を発行します。  
  
 **エラー C2228: '.operator *type*' の左側はクラス、構造体、共用体でなければなりません**     例 \(変更前\)  
  
    ```cpp  
    typedef int index_t; void bounds_check(index_t index); void login(int column) { bounds_check(column.operator index_t());  // error C2228 }  
    ```  
  
     例 \(変更後\)  
  
    ```cpp  
    typedef int index_t; void bounds_check(index_t index); void login(int column) { bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int' }  
    ```  
  
-   **詳細な型指定子の冗長な typename**  
  
     以前のバージョンのコンパイラでは、詳細な型指定子内で `typename` を指定できました。この方法で記述されたコードは意味的に正しくありません。 コンパイラはこの方法で記述されたコードを受け入れなくなりました。代わりにコンパイラ エラー C3406 を発行します。  
  
 **エラー C3406: 'typename' は詳細な型指定子では使用できません**     例 \(変更前\)  
  
    ```cpp  
    template <typename class T> class container;  
    ```  
  
     例 \(変更後\)  
  
    ```cpp  
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case class container;  
    ```  
  
-   **初期化子リストからの配列の型推論**  
  
     以前のバージョンのコンパイラでは、初期化子リストからの配列の型推論はサポートされていませんでした。 コンパイラでこの形式の型推論がサポートされるようになりました。その結果、初期化子リストを使用した関数テンプレートへの呼び出しがあいまいになったり、以前のバージョンのコンパイラとは異なるオーバーロードが選ばれたりする可能性があります。 これらの問題を解決するには、プログラマの意図したオーバーロードをプログラムが明示的に指定する必要があります。  
  
     この新しい動作により、オーバーロードの解決で過去の候補と同程度に優れた追加候補が検討されると、呼び出しはあいまいになり、結果としてコンパイラはコンパイラ エラー C2668 を発行します。  
  
 **エラー C2668: '*function*' : オーバーロード関数の呼び出しを解決することができません**     例 1: オーバーロード関数のあいまいな呼び出し \(変更前\)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...) template <typename... Args> void f(int, Args...);  // template <int N, typename... Args> void f(const int (&)[N], Args...); int main() { // The compiler now considers this call ambiguous, and issues a compiler error  f({3});  error C2668: 'f' ambiguous call to overloaded function }  
    ```  
  
     例 1: オーバーロード関数のあいまいな呼び出し \(変更後\)  
  
    ```cpp  
    template <typename... Args> void f(int, Args...);  // template <int N, typename... Args> void f(const int (&)[N], Args...); int main() { // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it. f(3); }  
    ```  
  
     この新しい動作により、オーバーロードの解決で過去の候補よりも適合度の高い追加候補が検討されると、呼び出しはあいまいにならずに新しい候補に解決され、プログラムの動作は変化します。これはプログラマの意図した動作とは異なる場合があります。  
  
     例 2: オーバーロードの解決の変更 \(変更前\)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...) struct S { int i; int j; }; template <typename... Args> void f(S, Args...); template <int N, typename... Args> void f(const int *&)[N], Args...); int main() { // The compiler now resolves this call to f(const int (&)[N], Args...) instead  f({1, 2}); }  
    ```  
  
     例 2: オーバーロードの解決の変更 \(変更後\)  
  
    ```cpp  
    struct S;  // as before template <typename... Args> void f(S, Args...); template <int N, typename... Args> void f(const int *&)[N], Args...); int main() { // To call f(S, Args...), perform an explicit cast to S on the initializer list. f(S{1, 2}); }  
    ```  
  
-   **switch ステートメントの警告の復元**  
  
     前のバージョンのコンパイラで、`switch` ステートメント関連の、以前から存在していた警告が削除されました。今ではこれらの警告は復元されています。 コンパイラは復元された警告を発行するようになり、特定の case \(既定の case を含む\) に関連する警告が、switch ステートメントの最後の行ではなく、問題のある case を含む行で発行されるようになりました。 この結果、以前とは異なる行でそれらの警告が発行されるようになり、以前は `#pragma warning(disable:####)` を使用して抑制できていた警告も、意図どおりに抑制できなくなる可能性があります。 意図どおりにこれらの警告を抑制するには、問題がある可能性のある最初の case の上の行まで `#pragma warning(disable:####)` ディレクティブを移動しなければならない場合があります。 復元された警告を次に示します。  
  
 **警告 C4060: switch ステートメントに 'case' または 'default' ラベルがありません。 警告 C4061: switch 中の列挙子 '*bit1*' \('*flags*' の\) は case ラベルによって明示的にハンドルされません 警告 C4062: switch 中の列挙子 '*bit1*' \('*flags*' の\) はハンドルされません 警告 C4063: case '*bit32*' は '*flags*' の switch の値として正しくありません 警告 C4064: 不完全な '*flags*' の switch です 警告 C4065: switch 文に 'default' ラベルはありますが 'case' ラベルがありません。 警告 C4808: case '*value*' は '*bool*' 型の switch ラベルには不適切です 警告 C4809: switch 文に冗長な 'default' ラベルが存在します。可能な 'case' 条件はすべて記述されています**     C4063 の例 \(変更前\)  
  
    ```cpp  
    class settings { public: enum flags { bit0 = 0x1, bit1 = 0x2, ... }; ... }; int main() { auto val = settings::bit1; switch (val) { case settings::bit0: break; case settings::bit1: break;  case settings::bit0 | settings::bit1:  // warning C4063 break; } };  
    ```  
  
     C4063 の例 \(変更後\)  
  
    ```cpp  
    class settings {...};  // as above int main() { // since C++11, use std::underlying_type to determine the underlying type of an enum typedef std::underlying_type<settings::flags>::type flags_t; auto val = settings::bit1; switch (static_cast<flags_t>(val)) { case settings::bit0: break; case settings::bit1: break; case settings::bit0 | settings::bit1:  // ok break; } };  
    ```  
  
     その他の復元の警告の例については、それらのドキュメントをご覧ください。  
  
-   **\#include: パス名で親ディレクトリの指定子 '..' を使用する** \(\/Wall \/WX にのみ影響\)  
  
     以前のバージョンのコンパイラでは、親ディレクトリの指定子の使用が検出されませんでした '… '  パス名で  `#include` ディレクティブです。 この方法で記述されたコードは通常、プロジェクトの相対パスが正しく使用されていないためにプロジェクトの外部に存在するヘッダーをインクルードすることを目的としています。 この従来の動作のせいで、プログラマが意図したものとは異なるソース ファイルをインクルードしてプログラムがコンパイルされる危険性や、これらの相対パスを他のビルド環境に移植できない危険性が生じました。 コンパイラは、この方法で書かれたコードを検出してプログラマに通知し、有効な場合にはオプションのコンパイラ警告 C4464 を発行するようになりました。  
  
 **警告 C4464: 相対インクルード パスに '..' が含まれています**     例 \(変更前\)  
  
    ```cpp  
    #include "..\headers\C4426.h"  // emits warning C4464  
    ```  
  
     例 \(変更後\)  
  
    ```cpp  
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories  
    ```  
  
     さらに、コンパイラは、特定の診断には影響を与えないがもお勧めする親ディレクトリの指定子".."  インクルード ディレクトリをプロジェクトのメモを定める必要があります。  
  
-   **\#pragma optimize\(\) がヘッダー ファイルの終わりを超える** \(\/Wall \/WX にのみ影響\)  
  
     以前のバージョンのコンパイラでは、翻訳単位内に含まれるヘッダー ファイルをエスケープする最適化フラグの設定の変更は検出されませんでした。 コンパイラは、この方法で書かれたコードを検出してプログラマに通知し、有効な場合には、問題のある `#include` の位置でオプションのコンパイラ警告 C4426 を発行するようになりました。 この警告が発行されるのは、この変更が、コンパイラに対するコマンドライン引数によって設定された最適化フラグと競合する場合のみです。  
  
 **警告 C4426: ヘッダーを含めた後で最適化フラグが変更されました。\#pragma optimize\(\) が原因であることが考えられます**     例 \(変更前\)  
  
    ```cpp  
    // C4426.h #pragma optimize("g", off) ... // C4426.h ends // C4426.cpp #include "C4426.h"  // warning C4426  
    ```  
  
     例 \(変更後\)  
  
    ```cpp  
    // C4426.h #pragma optimize("g", off) ... #pragma optimize("", on)  // restores optimization flags set via command-line arguments // C4426.h ends // C4426.cpp #include "C4426.h"  
    ```  
  
-   **\#pragma warning\(push\)** と **\#pragma warning\(pop\)** のミスマッチ \(\/Wall \/WX にのみ影響\)  
  
     以前のバージョンのコンパイラでは、`#pragma warning(push)` の状態の変更が、異なるソース ファイルの `#pragma warning(pop)` 状態の変更とペアになっていても \(故意であることはまれですが\)、それを検出しませんでした。この従来の動作のせいで、プログラマの意図と異なる一連の警告が有効な状態でプログラムがコンパイルされる危険性が生じ、結果として、問題のあるランタイム動作が警告なしに発生する原因となっていました。コンパイラは、この方法で書かれたコードを検出してプログラマに通知し、有効な場合には、一致する `#pragma warning(pop)` の位置でオプションのコンパイラ警告 C5031 を発行するようになりました。この警告には、対応する \#pragma warning\(push\) の場所を参照するメモが含まれます。  
  
 **警告 C5031: \#pragma warning\(pop\): 一致していない可能性があります。別のファイルにプッシュされた警告の状態を取り出している可能性があります**     例 \(変更前\)  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h ... #pragma warning(pop)  // pops a warning state not pushed in this source file ... // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling' ... #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031 ...   
    ```  
  
     例 \(変更後\)  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop)  // pops the warning state pushed in this source file // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h #pragma warning(push)  // pushes the warning state pushed in this source file #pragma warning(disable:####) ... #pragma warning(pop) // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order. ... #include "C5031_part2.h" ...   
    ```  
  
     一般的でありませんが、この方法で記述されたコードは意図的な場合もあります。この方法で記述されたコードは `#include` の順序の変更の影響を受けます。可能な場合は、自己完結型の方法を使用してソース コード ファイルで警告状態を管理することをお勧めします。  
  
-   **一致していない \#pragma warning\(push\)** \(\/Wall \/WX にのみ影響\)  
  
     以前のバージョンのコンパイラでは、翻訳単位の末尾で一致していない `#pragma warning(push)` の状態の変更は検出されませんでした。 コンパイラは、この方法で書かれたコードを検出してプログラマに通知し、有効な場合には、一致していない \#pragma warning\(push\) の位置でオプションのコンパイラ警告 C5032 を発行するようになりました。 この警告が発行されるのは、翻訳単位にコンパイル エラーがない場合のみです。  
  
 **警告 C5032: 対応する \#pragma warning\(pop\) がない \#pragma warning\(push\) が検出されました**     例 \(変更前\)  
  
    ```cpp  
    // C5032.h #pragma warning(push) #pragma warning(disable:####) ... // C5032.h ends without #pragma warning(pop) // C5032.cpp #include "C5032.h" ... // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h  
    ```  
  
     例 \(変更後\)  
  
    ```cpp  
    // C5032.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop) // matches #pragma warning (push) on line 1 // C5032.h ends // C5032.cpp #include "C5032.h" ... // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)  
    ```  
  
-   **\#pragma 警告状態の追跡が強化された結果、追加の警告が発行される場合があります。**  
  
     以前のバージョンのコンパイラでは、\#pragma 警告状態の変化の追跡が不十分なため、すべての意図された警告を発行できませんでした。 この動作により、プログラマの意図したものとは異なる状況で、事実上、特定の警告が抑制される危険性がありました。 コンパイラは \#pragma 警告状態をより確実に追跡するようになりました \(特にテンプレート内部での \#pragma 警告状態の変化に関連するもの\)。また `#pragma warning(push)` と `#pragma warning(pop)` の意図しない使用をプログラマが見つける手助けとして、新しい警告 C5031 と C5032 を必要に応じて発行するようになりました。  
  
     \#pragma 警告状態の変更の追跡が強化された結果、以前は誤って抑制されていた警告、または以前は誤って診断されていた問題に関連する警告が発行されるようになる場合があります。  
  
-   **制御が渡らないコードの識別の強化**  
  
     C\+\+ 標準ライブラリが変更されたり、以前のバージョンのコンパイラよりも関数呼び出しのインライン化機能が強化されたりしたため、コンパイラは特定のコードに制御が渡らないことを示せるようになりました。 この新しい動作の結果、警告 C4720 のインスタンスが新しく、あるいはより頻繁に発行される可能性があります。  
  
 **警告 C4720: 制御が渡らないコードです**     多くの場合、この警告が発行されるのは、最適化を有効にしてコンパイルするときだけです。最適化により、より多くの関数呼び出しがインライン化されたり、冗長なコードが削除されたり、コードに制御が渡っていないことを他の方法で判別できるようになったりするためです。 警告 C4720 の新しいインスタンスが try\/catch ブロックで頻繁に発生 \(特に [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True) の使用に関連して\) していることが確認されています。  
  
     例 \(変更前\)  
  
    ```cpp  
    try { auto iter = std::find(v.begin(), v.end(), 5); } catch(…) { do_something();  // ok }  
    ```  
  
     例 \(変更後\)  
  
    ```cpp  
    try { auto iter = std::find(v.begin(), v.end(), 5); } catch(…) { do_something();  // warning C4702: unreachable code }  
    ```