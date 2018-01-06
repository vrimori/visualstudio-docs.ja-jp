---
title: "SAL を理解する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 196bfdbeeda00199861ea2f676553f024fcaf98f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-sal"></a>SAL について
Microsoft ソース コード注釈言語 (SAL) は、そのパラメーターとそれが、それらについている前提条件と、それが完了したら、保証の関数の使用について説明するに使用できる注釈のセットを提供します。 注釈はヘッダー ファイルで定義されている`<sal.h>`です。 C++ 用の visual Studio コード分析では、SAL 注釈を使用して、関数の分析を変更します。 SAL 2.0 の Windows のドライバーの開発の詳細については、次を参照してください。 [SAL 2.0 注釈の Windows ドライバー](http://go.microsoft.com/fwlink/?LinkId=250979)です。  
  
 ネイティブ、C および C++ の目的および不変性を一貫して表現する開発者向けの限られた方法のみを提供します。 SAL 注釈を使用すると、それらを使用している開発者は、その使用方法を理解できるようにより詳細で関数を記述できます。  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>SAL の概要とそれを使用する理由  
 SAL は、簡単に言うと、コンパイラがコードを確認する安価な方法です。  
  
### <a name="sal-makes-code-more-valuable"></a>SAL でコードの価値を高める  
 SAL は、人とコード分析ツールの両方、コード デザインをわかりやすくするのに役立ちます。 C ランタイム関数を示す例を考えてみます`memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 この関数が何を指定することができますか。 関数が実装されているかと呼ばれる、プログラムの精度を確認する特定のプロパティを保持する必要があります。 例などの宣言を見るだけとは何かがわかりません。 SAL 注釈のないドキュメントやコードのコメントに依存する必要があります。 ここでは、MSDN のドキュメント`memcpy`といいます。  
  
> "コピーは、src を追加先のバイト数をカウントします。 ソースと変換先が重なり合う場合 memcpy の動作は定義されません。 Memmove を使用して、重なり合う領域を処理します。   
> **セキュリティに関する注意:**サイズ以上コピー元のバッファーにコピー先のバッファーが同じであることを確認してください。 詳細についてを参照してバッファー オーバーランの回避します。"  
  
 ドキュメントには、いくつかコードがプログラムの精度を確認する特定のプロパティを維持することを示している情報のビットにはが含まれています。  
  
-   `memcpy`コピー、`count`ソース バッファーからコピー先のバッファーにバイトです。  
  
-   コピー先のバッファーは、少なくともソース バッファーと同じサイズである必要があります。  
  
 ただし、コンパイラでは、ドキュメントや非公式のコメントを読み取ることができません。 2 つのバッファー間のリレーションシップがあることを認識していないと`count`、それも実質的に推測できないリレーションシップに関するとします。 SAL は、次のように、プロパティと、関数の実装に関するより明確を指定できます。  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 これらの注釈と似ています MSDN ドキュメント内の情報より簡潔になっているセマンティック パターンに従うことがわかります。 このコードを読み取るときに、この関数のプロパティとバッファー オーバーランのセキュリティの問題を回避する方法をすばやく理解できます。 さらに、SAL を提供するセマンティック パターンでは、効率と潜在的なバグの初期検出の自動コード分析ツールの有効性を改善できます。 このバグの実装を書き込みます誰か想像してみてください`wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 この実装には、一般的なものではオフ エラーが含まれています。 コードの作成者にバッファー サイズの SAL 注釈が含まれているさいわい、— コード分析ツールはこの関数のみを分析してバグをキャッチする可能性があります。  
  
### <a name="sal-basics"></a>SAL の基礎  
 SAL では、使用パターンによっては、分類、パラメーターの 4 つの基本的な種類を定義します。  
  
|カテゴリ|パラメーターの注釈|説明|  
|--------------|--------------------------|-----------------|  
|**呼び出される関数への入力します。**|`_In_`|データは、呼び出された関数に渡され、読み取り専用として扱われます。|  
|**入力が、関数を呼び出すし、呼び出し元に出力**|`_Inout_`|使用可能なデータは、関数に渡され、変更される可能性があります。|  
|**呼び出し元への出力**|`_Out_`|呼び出し元は、呼び出された関数に書き込むための領域のみを提供します。 呼び出された関数では、その領域にデータを書き込みます。|  
|**呼び出し元へのポインターの出力**|`_Outptr_`|同様に**呼び出し元に出力**です。 呼び出された関数によって返される値は、ポインターです。|  
  
 これら 4 つの基本的な注釈さまざまな方法でが明示的で行われたことができます。 既定では、注釈付きポインター パラメーターが必要になると想定: NULL でない必要がある関数が成功します。 基本的な注釈の最も一般的に使用されるバリエーションの 1 つは、ポインター パラメーターが省略可能であることを示します: NULL の場合、関数は成功する処理を行ってでします。  
  
 次の表は、必須パラメーターと省略可能なパラメーターを区別する方法を示します。  
  
||必須のパラメーターです。|パラメーターは省略可能|  
|-|-----------------------------|-----------------------------|  
|**呼び出される関数への入力します。**|`_In_`|`_In_opt_`|  
|**入力が、関数を呼び出すし、呼び出し元に出力**|`_Inout_`|`_Inout_opt_`|  
|**呼び出し元への出力**|`_Out_`|`_Out_opt_`|  
|**呼び出し元へのポインターの出力**|`_Outptr_`|`_Outptr_opt_`|  
  
 これらの注釈により、使用可能な初期化されていない値の識別し、正式かつ正確な方法で無効な null ポインターを使用します。 必須パラメーターに NULL を渡すと、クラッシュが発生する可能性があります。 または返される「失敗」のエラー コードが発生する可能性があります。 どちらにしても、関数は、そのジョブを実行成功ことはできません。  
  
## <a name="sal-examples"></a>SAL の例  
 このセクションでは、基本の SAL 注釈のコード例を示します。  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Visual Studio Code 分析ツールを使用して問題を検出する  
 例では、コードの欠陥を見つけるには、Visual Studio コード分析ツールを SAL 注釈と共に使用します。 実行する方法を次に示します。  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Visual Studio のコード分析ツールと SAL を使用するには  
  
1.  Visual Studio での SAL 注釈を含む C++ プロジェクトを開きます。  
  
2.  メニュー バーで、次のように選択します。**ビルド**、**ソリューションでコード分析を実行**です。  
  
     検討、_In\_のこのセクションの例です。 これでコード分析を実行する場合は、この警告が表示されます。  
  
    > **C6387 無効なパラメーター値**   
    > 'ポイント' が '0' にある可能性があります。 この動作 'InCallee' 関数の指定に従っていません。  
  
### <a name="example-the-in-annotation"></a>例: _In\_注釈  
 `_In_`注釈には、ことを示します。  
  
-   パラメーターは、有効にする必要がありは変更されません。  
  
-   関数はのみバッファーから読み取り、1 つの要素。  
  
-   呼び出し元は、バッファーを提供し、初期化する必要があります。  
  
-   `_In_`「読み取り専用」を指定します。 よくある間違いは、適用する`_In_`する必要のあるパラメーターに、`_Inout_`注釈代わりにします。  
  
-   `_In_`非ポインター スカラーにアナライザーによって無視されますが、使用できます。  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 呼び出し元が初期化済みのバッファーに Null 以外のポインターを渡すことを検証でこの例を Visual Studio コード分析を使用する場合`pInt`です。 この場合、`pInt`ポインターが NULL にすることはできません。  
  
### <a name="example-the-inopt-annotation"></a>例: _In_opt\_注釈  
 `_In_opt_`同じ`_In_`ただし、入力パラメーターが NULL にできるし、そのため、関数は、このチェックする必要があります。  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Visual Studio コード分析では、関数は、バッファーにアクセスする前に NULL の確認を検証します。  
  
### <a name="example-the-out-annotation"></a>例: _Out\_注釈  
 `_Out_`一般的なシナリオを要素バッファーを指す NULL ポインターが渡され、関数は、要素を初期化をサポートしています。 呼び出し元は呼び出しの前にバッファーを初期化する必要はありません。呼び出された関数は promise を返す前に初期化します。  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Visual Studio コード分析ツールは、呼び出し元がのバッファーに NULL 以外のポインターを渡すことを検証`pInt`を返す前に、バッファーが関数によって初期化されているとします。  
  
### <a name="example-the-outopt-annotation"></a>例: _Out_opt\_注釈  
 `_Out_opt_`同じ`_Out_`ただし、パラメーターを NULL にできるし、そのため、関数は、このチェックする必要があります。  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio コード分析では、この関数がより前に NULL を検査するを検証`pInt`が逆参照と if`pInt`を返す前に、関数によって、バッファーが初期化されている NULL でないです。  
  
### <a name="example-the-inout-annotation"></a>例: _Inout\_注釈  
 `_Inout_`関数によって変更されるポインター パラメーターの注釈に使用されます。 ポインターは、呼び出しの前に有効な初期化されたデータを指す必要がありますされ場合でも、変更が必要も有効な値に返された場合。 関数からの読み取りし、1 つの要素のバッファーに書き込むことがあります自由に注釈を指定します。 呼び出し元は、バッファーを提供し、初期化する必要があります。  
  
> [!NOTE]
>  同様に`_Out_`、`_Inout_`変更可能な値に適用する必要があります。  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // 'pInt' should not be NULL  
}  
  
```  
  
 Visual Studio コード分析では、呼び出し元が初期化済みのバッファーに NULL 以外のポインターを渡すことを検証`pInt`、戻る前に、その`pInt`も null でないバッファーを初期化します。  
  
### <a name="example-the-inoutopt-annotation"></a>例: _Inout_opt\_注釈  
 `_Inout_opt_`同じ`_Inout_`ただし、入力パラメーターが NULL にできるし、そのため、関数は、このチェックする必要があります。  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio コード分析では、この関数は、バッファーにアクセスする前に、null チェックを検証`pInt`を返す前に、関数によって、バッファーが初期化されている NULL でないです。  
  
### <a name="example-the-outptr-annotation"></a>例: _Outptr\_注釈  
 `_Outptr_`ポインターを返すためのものでは、パラメーターの注釈に使用されます。  自体はパラメーターが NULL の場合、することはできません、呼び出された関数内の NULL ポインターを返し、初期化されたデータを指すポインターです。  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Visual Studio コード分析では、呼び出し元が NULL 以外のポインターを渡すことを検証`*pInt`を返す前に、関数によって、バッファーが初期化されているとします。  
  
### <a name="example-the-outptropt-annotation"></a>例: _Outptr_opt\_注釈  
 `_Outptr_opt_`同じ`_Outptr_`パラメーターが省略可能なことを除いて、-、呼び出し元が NULL ポインターでパラメーターに渡すことができます。  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Visual Studio コード分析では、この関数がより前に NULL を検査するを検証`*pInt`が逆参照を返す前に、バッファーが関数によって初期化されているとします。  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>例: _Success\_ (_o) と組み合わせて注釈\_  
 注釈は、ほとんどのオブジェクトに適用できます。  具体的には、全体の関数の注釈を付けることができます。  関数の最も基本的な特性の 1 つは、成功または失敗にすることができます。 関連付け、バッファーのサイズと同様に、C と C++ を関数の成功または失敗が express ことはできません。 使用して、`_Success_`注釈を次のように、関数の成功を言うことができます。  パラメーターを`_Success_`注釈は式が true の場合に、関数が成功したことを示すことだけです。 式には、注釈のパーサーを処理できるものを指定できます。 関数から制御が戻た後の注釈の効果を適用できるは、関数が成功した場合だけです。 この例ではどのように`_Success_`対話`_Out_`を正しいことを行うには。 キーワードを使用することができます`return`を戻り値を表します。  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 `_Out_`注釈と、Visual Studio コード分析の検証を渡すことを呼び出し元は、NULL ポインターを格納するバッファーを`pInt`、返す前に、関数によって、バッファーが初期化されているとします。  
  
## <a name="sal-best-practice"></a>SAL のベスト プラクティス  
  
### <a name="adding-annotations-to-existing-code"></a>既存のコードに注釈を追加する  
 SAL は、セキュリティと、コードの信頼性を向上するのに役立つ強力なテクノロジです。 SAL を習得すると後、は、毎日の仕事に新しいスキルを適用できます。 新しいコードでは、全体にわたって; 仕様 SAL ベースの仕様を使用できます。以前のコードには、段階的に注釈を追加し、更新するたびに利点を向上させるできます。  
  
 Microsoft パブリック ヘッダーの注釈が既に付けられています。 したがって、こと、プロジェクト内で最初に注釈を付けるとリーフ ノードの関数とを最大限に活用する Win32 Api を呼び出す関数をお勧めします。  
  
### <a name="when-do-i-annotate"></a>注釈を付けるタイミング  
 次にいくつかのガイドラインを示します。  
  
-   すべてのポインター パラメーターの注釈を設定します。  
  
-   コード分析はバッファーおよびポインターの安全を確保できるように、値の範囲の注釈を注釈を付けます。  
  
-   ルールのロックおよびロックの副作用の注釈を設定します。 詳細については、次を参照してください。[ロック動作の注釈を付ける](../code-quality/annotating-locking-behavior.md)です。  
  
-   ドライバーのプロパティおよびその他のドメイン固有のプロパティの注釈を設定します。  
  
 または、すべてのパラメーター全体で意図的にクリアして、注釈が実行されていることを確認するが簡単に注釈を付けることができます。  
  
## <a name="related-resources"></a>関連資料  
 [コード分析チームのブログ](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>参照  
 [C/C++ コード障害を減らす SAL 注釈の使用](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [関数パラメーターおよび戻り値の注釈を付ける](../code-quality/annotating-function-parameters-and-return-values.md)   
 [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [注釈を適用するタイミングと場所を指定します。](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)