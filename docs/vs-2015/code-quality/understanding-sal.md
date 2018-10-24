---
title: SAL の理解 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: be3d54921f7bc3a74c858340f28b68b03497939a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874281"
---
# <a name="understanding-sal"></a>SAL について
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft ソース コード注釈言語 (SAL) では、関数がそのパラメーターや、それらについて行う想定を終了するときに行う保証を使用する方法について説明するために使用できる注釈のセットを提供します。 注釈はヘッダー ファイルで定義されている`<sal.h>`します。 C++ 用の visual Studio コード分析では、SAL 注釈を使用して、関数の分析を変更します。 Windows ドライバー開発の SAL 2.0 の詳細については、次を参照してください。 [Windows ドライバーの SAL 2.0 注釈](http://go.microsoft.com/fwlink/?LinkId=250979)します。  
  
 ネイティブ、C および C++ 開発者の意図と不変性が一貫して express の制限がありますのみを提供します。 SAL 注釈を使用すると、それらを使用する開発者は、その使用方法を理解できるようにより詳細で関数を記述できます。  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>SAL の概要とそれを使用する理由  
 簡単に言えば、SAL は、コンパイラのコードを確認できるようにする安価な方法です。  
  
### <a name="sal-makes-code-more-valuable"></a>SAL でコードの価値を高める  
 SAL は、人間とコード分析ツールの両方、コード デザインをわかりやすくするのに役立ちます。 C ランタイム関数を示す例を検討`memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 この関数の動作とわかりますか。 関数が実装されているかと呼ばれる、特定のプロパティをプログラムの正確性を確実に維持する必要があります。 この例のなどの宣言を見るだけでは何かがわかりません。 、SAL 注釈のないドキュメントやコードのコメントに依存する必要があります。 ここでの MSDN ドキュメントは、`memcpy`といいます。  
  
> "コピーは、src を取引先のバイト数をカウントします。 ソースとコピー先 memcpy の動作は未定義です。 Memmove を使用して、重複する領域を処理します。   
> **セキュリティに関する注意:** サイズまたはソース バッファーより大きいコピー先のバッファーが同じであることを確認してください。 詳細についてを参照してバッファー オーバーランの回避します。"  
  
 ドキュメントには、いくつかプログラムの正確性を確実に特定のプロパティを維持するために、コードが提案する情報のビットにはが含まれています。  
  
- `memcpy` コピー、`count`の元のバッファーからコピー先のバッファーのバイト。  
  
- コピー先のバッファーは少なくともソース バッファーと同じ大きさである必要があります。  
  
  ただし、コンパイラでは、ドキュメントまたは非公式のコメントを読み取ることができません。 2 つのバッファーの間のリレーションシップがあることを認識していないと`count`、それも効果的に推測できないリレーションシップに関するとします。 次に示すよう、SAL はプロパティと、関数の実装についてわかりやすくするために提供できます。  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 MSDN ドキュメントの情報は、これらの注釈のようになりますが、これらには、簡潔なし、セマンティックのパターンに従うに注意してください。 このコードを読み、この関数のプロパティとバッファー オーバーランのセキュリティの問題を回避する方法をすばやく理解できます。 さらに、潜在的なバグの早期発見に自動化されたコード分析ツールの効率性および SAL を提供するセマンティック パターンを向上させることができます。 たとえば、だれかがこのバグの実装を記述`wmemcpy`:  
  
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
  
 この実装には、一般的なものではオフ エラーが含まれています。 コードの作成者は、幸いにも、バッファー サイズの SAL 注釈に含まれる場合、コード分析ツールは、この関数のみを分析することで、バグを捕捉できます。  
  
### <a name="sal-basics"></a>SAL の基礎  
 SAL は、使用パターンによって分類のパラメーターの 4 つの基本的な種類を定義します。  
  
|カテゴリ|パラメーターの注釈|説明|  
|--------------|--------------------------|-----------------|  
|**入力に関数が呼び出されます**|`_In_`|データは、呼び出された関数に渡され、読み取り専用として扱われます。|  
|**呼び出し元に力を呼び出した関数への入力**|`_Inout_`|使用可能なデータは、関数に渡され、変更される可能性があります。|  
|**呼び出し元への出力**|`_Out_`|呼び出し元は、呼び出された関数への書き込みを行うための領域のみを提供します。 呼び出された関数では、その領域にデータを書き込みます。|  
|**呼び出し元へのポインターの出力**|`_Outptr_`|ような**呼び出し元に出力**します。 呼び出し先関数によって返される値は、ポインターです。|  
  
 これら 4 つの基本的な注釈でさまざまな方法がより明確な行われたことができます。 既定では、注釈付きのポインター パラメーターが必要になると想定: NULL でない必要がある関数が成功します。 最もよく使用される基本的な注釈のバリエーションは、ポインター パラメーターが省略可能であることを示します: NULL の場合、関数は、その作業を行うには成功もします。  
  
 このテーブルは、必須およびオプションのパラメーターを区別する方法を示します。  
  
||パラメーターが必須です。|パラメーターは省略可能|  
|-|-----------------------------|-----------------------------|  
|**入力に関数が呼び出されます**|`_In_`|`_In_opt_`|  
|**呼び出し元に力を呼び出した関数への入力**|`_Inout_`|`_Inout_opt_`|  
|**呼び出し元への出力**|`_Out_`|`_Out_opt_`|  
|**呼び出し元へのポインターの出力**|`_Outptr_`|`_Outptr_opt_`|  
  
 これらの注釈可能な初期化されていない値を識別し、無効な null ポインターが、正式かつ正確な方法で使用します。 、クラッシュが発生する可能性があります、必須のパラメーターに NULL を渡すか、返される「失敗」のエラー コードが発生する可能性があります。 どちらの方法でも、関数は、そのジョブの実行に失敗することはできません。  
  
## <a name="sal-examples"></a>SAL の例  
 このセクションでは、基本の SAL 注釈のコード例を示します。  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Visual Studio Code 分析ツールを使用して問題を検出する  
 例では、Visual Studio コード分析ツールは、コードの欠陥を見つけるに SAL 注釈と共に使用されます。 その方法を次に示します。  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Visual Studio のコード分析ツールと SAL を使用するには  
  
1. Visual Studio での SAL 注釈を含む C++ プロジェクトを開きます。  
  
2. メニュー バーで、**ビルド**、**ソリューションでコード分析を実行**します。  
  
    検討してください、\_で\_のこのセクションの例です。 これでコード分析を実行する場合は、この警告が表示されます。  
  
   > **C6387 無効なパラメーター値**   
   > 'pInt' の '0' 可能性があります。 これは、'InCallee' 関数の仕様に準拠していません。  
  
### <a name="example-the-in-annotation"></a>例:\_で\_注釈  
 `_In_`注釈には、ことを示します。  
  
-   パラメーターが有効にする必要がありは変更されません。  
  
-   関数は、1 つの要素のバッファーからのみ読み取ります。  
  
-   呼び出し元は、バッファーを提供し、初期化する必要があります。  
  
-   `_In_` 「読み取り専用」を指定します。 よくある間違いは、適用する`_In_`が必要なパラメーターに、`_Inout_`注釈代わりにします。  
  
-   `_In_` 非ポインター スカラーのアナライザーによって無視が許可されます。  
  
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
  
 呼び出し元が初期化されたバッファーに Null 以外のポインターを渡すことを検証でこの例を Visual Studio コード分析を使用する場合`pInt`します。 この場合、`pInt`ポインターが NULL にすることはできません。  
  
### <a name="example-the-inopt-annotation"></a>例: \_In_opt\_注釈  
 `_In_opt_` 同じ`_In_`, 点が、入力パラメーターが NULL にできるし、この関数がそのため、確認する必要があります。  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Visual Studio コード分析は、関数は、バッファーにアクセスする前に null チェックを検証します。  
  
### <a name="example-the-out-annotation"></a>例:\_アウト\_注釈  
 `_Out_` 要素のバッファーを指す NULL ポインターが渡され、関数が要素を初期化します、一般的なシナリオをサポートしています。 呼び出し元は呼び出しの前にバッファーを初期化する必要はありません。呼び出された関数を返す前に初期化する約束します。  
  
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
  
 Visual Studio コード分析ツールの検証呼び出し元がのバッファーに NULL 以外のポインターを渡し`pInt`を返す前に、関数によってバッファーが初期化されているとします。  
  
### <a name="example-the-outopt-annotation"></a>例: \_Out_opt\_注釈  
 `_Out_opt_` 同じ`_Out_`, 点が、パラメーターが NULL にできるし、この関数がそのため、確認する必要があります。  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio コード分析は、この関数をチェックする前に null を検証します`pInt`が逆参照される場合に`pInt`を返す前に、関数によってバッファーが初期化されている NULL でないです。  
  
### <a name="example-the-inout-annotation"></a>例: \_Inout\_注釈  
 `_Inout_` 関数によって変更されるポインター パラメーターの注釈に使用されます。 ポインターは、呼び出しの前に有効な初期化データを指す必要がありますされ、変わる場合でもが必要も有効な値を返された場合。 注釈は、関数の読み取りし、書き込みを 1 つの要素のバッファーに自由に可能性があることを指定します。 呼び出し元は、バッファーを提供し、初期化する必要があります。  
  
> [!NOTE]
>  ような`_Out_`、`_Inout_`変更可能な値に適用する必要があります。  
  
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
   InOutCallee(pInt); // ‘pInt’ should not be NULL  
}  
  
```  
  
 Visual Studio コード分析は、呼び出し元が初期化されたバッファーに NULL 以外のポインターを渡すことを検証します。 `pInt`、する前に返された場合に、`pInt`も null でないバッファーが初期化されます。  
  
### <a name="example-the-inoutopt-annotation"></a>例: \_Inout_opt\_注釈  
 `_Inout_opt_` 同じ`_Inout_`, 点が、入力パラメーターが NULL にできるし、この関数がそのため、確認する必要があります。  
  
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
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio コード分析は、この関数は、バッファーにアクセスする前に、null チェックを検証します。`pInt`がを返す前に、関数によってバッファーが初期化されている NULL でないです。  
  
### <a name="example-the-outptr-annotation"></a>例: \_Outptr\_注釈  
 `_Outptr_` ポインターを返すためのものがパラメーターの注釈に使用されます。  パラメーター自体が null の場合、することはできず、呼び出された関数では、NULL 以外のポインターを返しますが初期化されたデータを指すポインター。  
  
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
  
 Visual Studio コード分析は、呼び出し元が NULL 以外のポインターを渡すことを検証します`*pInt`を返す前に、関数によってバッファーが初期化されているとします。  
  
### <a name="example-the-outptropt-annotation"></a>例: \_Outptr_opt\_注釈  
 `_Outptr_opt_` 同じ`_Outptr_`パラメーターが省略可能なことを除いて、-、呼び出し元が NULL ポインターでパラメーターに渡すことができます。  
  
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
   *pInt = pInt2; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Visual Studio コード分析は、この関数をチェックする前に null を検証します`*pInt`が逆参照を返す前に、関数によってバッファーが初期化されているとします。  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>例:\_成功\_注釈と組み合わせて\_アウト\_  
 注釈は、ほとんどのオブジェクトに適用できます。  具体的には、全体の関数の注釈を付けることができます。  関数の最も明確な特性の 1 つは、成功または失敗にすることができます。 バッファーとそのサイズ間の関連付けのように、[C/C++] を関数の成功または失敗 express ことはできません。 使用して、`_Success_`注釈、関数の成功を言うことができます。  パラメーターを`_Success_`注釈はこれが true の場合に、関数が成功したことが示されている式だけです。 注釈パーサーが処理できる任意の式を指定できます。 関数から制御が戻た後の注釈の効果を適用できるは、関数が成功した場合だけです。 この例ではどのように`_Success_`対話`_Out_`は正常に実行します。 キーワードを使用する`return`を戻り値を表します。  
  
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
  
 `_Out_`注釈と Visual Studio のコード分析を検証する呼び出し元がのバッファーに NULL 以外のポインターを渡し`pInt`、返す前に、関数によってバッファーが初期化されているとします。  
  
## <a name="sal-best-practice"></a>SAL のベスト プラクティス  
  
### <a name="adding-annotations-to-existing-code"></a>既存のコードに注釈を追加する  
 SAL は、セキュリティとコードの信頼性を向上するのに役立つ強力なテクノロジです。 SAL について説明しますと後、は、日常の作業に新しいスキルを適用できます。 新しいコードは、設計全体で; SAL ベースの仕様を使用できます。以前のコードでは、段階的に注釈を追加し、更新するたびにメリットを向上させることができます。  
  
 Microsoft はパブリック ヘッダーが既に注釈が付いています。 そのため、あるプロジェクトで最初に注釈を付けるリーフ ノードの関数と関数を最大限に活用する Win32 Api を呼び出すをお勧めします。  
  
### <a name="when-do-i-annotate"></a>注釈を付けるタイミング  
 いくつかのガイドラインを次に示します。  
  
- すべてのポインター パラメーターの注釈を設定します。  
  
- 注釈の値の範囲の注釈を設定して、コード分析は、バッファーとポインターの安全を確保できるようにします。  
  
- ルールのロックおよびロックの副作用の注釈を設定します。 詳細については、次を参照してください。[ロック動作の注釈を付ける](../code-quality/annotating-locking-behavior.md)します。  
  
- ドライバーのプロパティとその他のドメイン固有のプロパティの注釈を設定します。  
  
  または、全体にわたって、インテントをオフにして、注釈が実行されていることを確認するが簡単にすべてのパラメーターの注釈を付けることができます。  
  
## <a name="related-resources"></a>関連資料  
 [コード分析チームのブログ](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>関連項目  
 [SAL 注釈を使用して C/C++ のコード障害を減らす](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)   
 [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)   
 [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [注釈を適用するタイミングと場所を指定します。](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)



