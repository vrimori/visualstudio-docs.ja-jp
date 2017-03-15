---
title: "Visual C++ 2015 Update 2 での互換性に影響する変更点 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5545ce3f-d8da-4007-88b7-8dba7dcd4d10
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mithom"
---
# Visual C++ 2015 Update 2 での互換性に影響する変更点
Visual C\+\+ 2015 Update 2 CTP にアップグレードすると、以前に正常にコンパイルと実行ができたコードでコンパイル エラーやランタイム エラーが発生する場合があります。 コンパイラとランタイムの動作でこのような問題を引き起こす変更は*互換性に影響する変更*と呼ばれ、通常は C\+\+ 言語標準、関数シグネチャ、メモリ内のオブジェクトのレイアウトの変更によって必要となります。  
  
 ここからは、Visual C\+\+ 2015 Update 2 CTP の特定の互換性に影響する変更点について説明します。この記事における「新しい動作」または「現在」という語は、そのバージョンを指します。 「従来の動作」や「以前」という語は、Visual C\+\+ 2015 Update 1 以前のリリースを指します。 Visual C\+\+ 2015 の初期リリースと Visual C\+\+ 2015 Update 1 の間の互換性に影響する変更点については、「[Update 1 での互換性に影響する変更点](../misc/breaking-changes-in-visual-cpp-2015-update-1.md)」をご覧ください。 Visual C\+\+ 2013 と Visual C\+\+ 2015 の間の互換性に影響する変更点については、「[Visual C\+\+ 2015 での互換性に影響する変更点](/visual-cpp/porting/visual-cpp-change-history-2003-20151)」をご覧ください。  
  
-   [コンパイラの互換性に影響する変更点](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Visual C\+\+ コンパイラ  
  
-   **SFINAE 式の部分的なサポートの結果として、追加の警告とエラーが発行される場合がある**  
  
     以前のバージョンのコンパイラは、SFINAE 式のサポートがなかったため、`decltype` 指定子内の特定の種類の式を解析しませんでした。 この従来の動作は正しい動作ではなく、C\+\+ 標準に準拠していません。 コンパイラは、継続的な適合性の向上により、これらの式を解析し、SFINAE 式を部分的にサポートするようになりました。 その結果、コンパイラは、以前のバージョンのコンパイラが解析しなかった式で検出された警告とエラーを発行します。  
  
     この新しい動作が、まだ宣言されていない型を含む `decltype` 式を解析するとき、コンパイラは結果としてコンパイラ エラー C2039 を発行します。  
  
 **エラー C2039: *'type'*: は *''global namespace''* のメンバーではありません**     例 1: 宣言されていない型の使用 \(変更前\)  
  
    ```cpp  
    struct s1  
    {  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  // error C2039  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     例 1 \(変更後\)  
  
    ```cpp  
    struct s1  
    {  
      template <typename>  // forward declare s2struct s2;  
  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     依存名が型であることを指定するために必要な `typename` キーワードが欠落している `decltype` 式がこの新しい動作によって解析されると、コンパイラは、コンパイラ エラー C2923 と共にコンパイラの警告 C4346 を発行します。  
  
 **警告 C4346: *'S2\<T\>::Type'*: 依存名は型ではありません エラー C2923: *'s1'*: *'S2\<T\>::Type'* は、パラメーター *'T'* の有効なテンプレート型引数ではありません**     例 2: 依存名が型ではない \(変更前\)  
  
    ```cpp  
    template <typename T>  
    struct s1  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    struct s2  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923  
    };  
    ```  
  
     例 2 \(変更後\)  
  
    ```cpp  
    template <typename T> struct s1 {...};  // as above  
    template <typename T> struct s2 {...};  // as above  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));  
    };  
    ```  
  
-   `volatile` **メンバー変数が、暗黙的に定義されたコンストラクターと代入演算子を防止する**  
  
     以前のバージョンのコンパイラは、`volatile` メンバー変数を持つクラスが、自動的に生成された既定のコピー\/移動コンストラクターと既定のコピー\/移動代入演算子を持つことを許可していました。 この従来の動作は正しい動作ではなく、C\+\+ 標準に準拠していません。 コンパイラは、揮発性のメンバー変数を持つクラスが、非単純コンストラクションと代入演算子を持つとみなすようになりました。それにより、これらの演算子の既定の実装が自動的に生成されることを防止します。  そのようなクラスが共用体 \(またはクラス内の無名共用体\) のメンバーである場合は、共用体のコピー\/移動コンストラクターとコピー\/移動代入演算子 \(または無名共用体を含むクラス\) は、暗黙的に削除済みとして定義されます。 明示的に定義することなく、共用体 \(または無名共用体を含むクラス\) を構築またはコピーしようとするとエラーとなり、結果として、コンパイラはコンパイラ エラー C2280 を発行します。  
  
 **エラー C2280: *'B::B\(const B &\)'*: 削除された関数を参照しようとしています**     例 \(変更前\)  
  
    ```cpp  
    struct A  
    {  
      volatile int i;  
      volatile int j;  
    };  
  
    extern A* pa;  
  
    struct B  
    {  
      union  
      {  
        A a;  
        int i;  
      };  
    };  
  
    B b1 {*pa};  
    B b2 (b1);  // error C2280  
    ```  
  
     例 \(変更後\)  
  
    ```cpp  
    struct A  
    {  
      int i;int j;  
    };  
  
    extern volatile A* pa;  
  
    A getA()  // returns an A instance copied from contents of pa  
    {  
      A a;  
      a.i = pa->i;  
      a.j = pa->j;  
      return a;  
    }  
  
    struct B;  // as above  
  
    B b1 {GetA()};  
    B b2 (b1);  // error C2280  
    ```  
  
-   **静的メンバー関数は、CV 修飾子をサポートしていません。**  
  
     以前のバージョンの Visual C\+\+ 2015 は、静的メンバー関数が CV 修飾子を持つことを許可していました。 この動作は、Visual C\+\+ 2015 および Visual C\+\+ 2015 Update 1 での回帰が原因です。Visual C\+\+ 2013 および Visual C\+\+ の以前のバージョンは、この方法で記述されたコードを拒否します。 Visual C\+\+ 2015 および Visual C\+\+ 2015 Update 1 の動作は正しいものではなく、C\+\+ 標準に準拠していません。  Visual Studio 2015 Update 2 は、この方法で記述されたコードを拒否し、コンパイラ エラー C2511 を代わりに発行します。  
  
 **エラー C2511: 'void A::func\(void\) const': オーバーロード メンバー関数は 'A' で見つかりませんでした**     例 \(変更前\)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() const {}  // C2511  
  
    ```  
  
     例 \(変更後\)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() {}  // removed const  
  
    ```  
  
-   **列挙型の事前宣言は、WinRT コードでは許可されていません** \(\/ZW にのみ影響\)  
  
     管理された C\+\+ コードが \/clr コンパイラ スイッチを使用して .Net Framework 用にコンパイルされる場合と同様に、Windows ランタイム \(WinRT\) 用にコンパイルされたコードは、`enum` 型が事前に宣言されることを許可しません。 この動作により、列挙型のサイズが常にわかり、WinRT 型システムに正しくプロジェクションを実行することができます。 コンパイラは、この方法で記述されたコードを拒否し、コンパイラ エラー C3197 と共にコンパイラ エラー C2599 を発行します。  
  
 **エラー C2599: *'CustomEnum'*: WinRT 列挙型の事前宣言は許可されていません エラー C3197: *'public'*: 定義でのみ使用することができます**     例 \(変更前\)  
  
    ```cpp  
    namespace A {  
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197  
    }  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
     例 \(変更後\)  
  
    ```cpp  
  
              // forward declaration of CustomEnum removed  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
-   **オーバーロードされた非メンバー operator new と operator delete をインラインで宣言できない** \(レベル 1 \(\/W1\) 既定で有効\)  
  
     以前のバージョンのコンパイラは、非メンバー operator new と operator delete 関数がインラインで宣言されるときに警告を発行しません。 この方法で記述されたコードは、形式が正しくなく \(診断は必要なし\)、new 演算子と delete 演算子の不一致 \(特に、サイズ割り当て解除と共に使用された場合\) から生じるメモリの問題を引き起こす可能性があります。この問題を診断するのは難しい場合があります。   コンパイラは警告 C4595 を発行するようになったので、この方法で記述されたコードを識別しやすくなりました。  
  
 **警告 C4595: *'operator new'*: 非メンバー new 演算子または delete 演算子の関数はインラインでは宣言できません**     例 \(変更前\)  
  
    ```cpp  
  
              inline void* operator new(size_t sz)  // warning C4595  
    {  
      ...  
    }  
    ```  
  
     例 \(変更後\)  
  
    ```cpp  
  
              void* operator new(size_t sz)  // removed inline  
    {  
      ...  
    }  
    ```  
  
     この方法で記述されたコードを修正するには、演算子の定義をヘッダー ファイルから対応するソース ファイルに移動することが必要な場合があります。