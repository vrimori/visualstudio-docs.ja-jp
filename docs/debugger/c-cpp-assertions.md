---
title: "C と C++ アサーション |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 46ea417ccd8b4dbecd0c6584699e9f2e98330d69
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cc-assertions"></a>アサーション
アサート ステートメントでは、プログラム内で true になる必要のある条件を指定します。 その条件が true でない場合、アサーションは失敗し、プログラムの実行が中断されると、および[アサートに失敗しました ダイアログ ボックス](../debugger/assertion-failed-dialog-box.md)が表示されます。  
  
 Visual C++ は、次の構成に基づくアサート ステートメントをサポートします。  
  
-   MFC アサーション (MFC プログラムの場合)  
  
-   [ATLASSERT](http://msdn.microsoft.com/Library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3) ATL を使用するプログラム  
  
-   CRT アサーション (C ランタイム ライブラリを使用するプログラムの場合)  
  
-   ANSI [assert 関数](/cpp/c-runtime-library/reference/assert-macro-assert-wassert)他の C/C++ プログラムです。  
  
 アサーションを使用して論理エラーを検出し、操作の結果を確認することで、処理する必要があるエラー条件をテストできます。  
  
##  <a name="BKMK_In_this_topic"></a> このトピックの内容  
 [アサーションのしくみ](#BKMK_How_assertions_work)  
  
 [デバッグ ビルドとリリース ビルドでのアサーション](#BKMK_Assertions_in_Debug_and_Release_builds)  
  
 [アサーションの副作用](#BKMK_Side_effects_of_using_assertions)  
  
 [CRT アサーション](#BKMK_CRT_assertions)  
  
 [MFC アサーション](#BKMK_MFC_assertions)  
  
-   [MFC ASSERT_VALID と cobject::assertvalid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  
  
-   [AssertValid に関する制限事項](#BKMK_Limitations_of_AssertValid)  
  
 [アサーションの使用](#BKMK_Using_assertions)  
  
-   [論理エラーの検出](#BKMK_Catching_logic_errors)  
  
-   [結果を確認します。](#BKMK_Checking_results_)  
  
-   [未処理の検索エラー](#BKMK_Testing_error_conditions_)  
  
##  <a name="BKMK_How_assertions_work"></a>アサーションのしくみ  
 MFC ライブラリまたは C ランタイム ライブラリのアサーションによってデバッガーが停止したとき、ソース ファイルが利用可能である場合は、そのソース ファイル内のアサーションが発生した位置にジャンプします。 両方にアサーション メッセージが表示されます、[出力ウィンドウ](../ide/reference/output-window.md)と**アサーションが失敗した** ダイアログ ボックス。 アサーション メッセージをコピーすることができます、**出力**を今後の参照を保存する場合は、テキスト ウィンドウへのウィンドウ。 **出力**ウィンドウも他のエラー メッセージを含めることがあります。 アサーションが失敗した原因を突き止める手掛かりとなるため、これらのエラー メッセージをよく調べてください。  
  
 開発中にアサーションを使用してエラーを検出します。 一般的に、想定ごとに 1 つのアサーションを使用します。 たとえば、引数が NULL でないと想定した場合、アサーションを使用してその想定が正しいかどうかをテストします。  
  
 [このトピックの内容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a>デバッグ ビルドとリリース ビルドでのアサーション  
 アサート ステートメントは、`_DEBUG` が定義されている場合のみコンパイルされます。 定義されていない場合、コンパイラはアサーションを null ステートメントとして扱います。 したがって、プログラムの最終リリース バージョンではアサート ステートメントのオーバーヘッドやパフォーマンス コストはゼロになります。`#ifdef` ディレクティブを使用する必要もありません。  
  
##  <a name="BKMK_Side_effects_of_using_assertions"></a>アサーションの副作用  
 アサーションをコードに追加するときは、そのアサーションに副作用がないことを確認してください。 たとえば、`nM` 値を変更する次のアサーションを考えます。  
  
```  
ASSERT(nM++ > 0); // Don't do this!  
  
```  
  
 `ASSERT` 式はプログラムのリリース バージョンでは評価されないため、`nM` の値は、デバッグ バージョンとリリース バージョンとでは異なります。 MFC では、この問題を避けるためには、使用することができます、[を確認してください](http://msdn.microsoft.com/Library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96)の代わりにマクロ`ASSERT`です。  `VERIFY`すべてのバージョンで式を評価しますが、リリース バージョンで結果はチェックしません。  
  
 アサート ステートメントで関数を呼び出す場合は、その関数の評価によって予想外の副作用が生じることがあるため特に注意してください。  
  
```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  
  
 `VERIFY` は、デバッグ バージョンでもリリース バージョンでも `myFnctn` を呼び出すため、安全に使用できます。 ただし、`VERIFY` を使用すると、リリース バージョンで不要な関数呼び出しのオーバーヘッドが発生します。  
  
 [このトピックの内容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_CRT_assertions"></a>CRT アサーション  
 CRTDBG です。H ヘッダー ファイルを定義、 [_assert マクロと _ASSERTE マクロ](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros)アサーションをチェックするためです。  
  
|マクロ|結果|  
|-----------|------------|  
|`_ASSERT`|指定した式が FALSE と評価された場合、`_ASSERT` 対象のファイル名と行番号を出力します。|`_ASSERTE`|  
|`_ASSERTE`|`_ASSERT` と同様の結果と共に、アサートされた式の文字列形式も出力します。|  
  
 FALSE と評価されたアサート対象の式もレポートするため、`_ASSERTE` マクロの方が強力です。 このマクロを使用すると、ソース コードを参照しなくても問題を識別できます。 ただし、アプリケーションのデバッグ バージョンに、`_ASSERTE` を使用してアサートした式ごとに文字列定数が含まれることになります。 `_ASSERTE` マクロを多用すると、これらの文字列式がかなりのメモリを占有します。 これが問題となる場合は、`_ASSERT` マクロを使用してメモリを節約してください。  
  
 `_DEBUG` が定義されている場合、`_ASSERTE` マクロは次のように定義されます。  
  
```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  
  
 アサートされた式が FALSE に評価された場合に[_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) (既定では、[メッセージ] ダイアログ ボックスを使用して) アサーション失敗をレポートするために呼び出されます。 選択した場合**を再試行してください**メッセージ ダイアログ ボックスで`_CrtDbgReport`1 を返しますと`_CrtDbgBreak`使用してデバッガーを呼び出す`DebugBreak`です。  
  
### <a name="checking-for-heap-corruption"></a>ヒープ破損のチェック  
 次の例で[_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory)ヒープの破損をチェックします。  
  
```  
_ASSERTE(_CrtCheckMemory());  
```  
  
### <a name="checking-pointer-validity"></a>ポインターの有効性チェック  
 次の例で[_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer)指定したメモリ範囲が読み取りや書き込みに対して有効であることを確認します。  
  
```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  
  
 次の例で[_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer)へのポインターがローカル ヒープ内にメモリを指すことを確認する (ヒープが作成され、C ランタイム ライブラリのこのインスタンスによって管理されている — DLL は、ライブラリの独自のインスタンスを持つことができ、したがって、独自のヒープ、アプリケーション ヒープの外部)。 このアサーションは、null アドレスや範囲外のアドレスだけでなく、静的変数、スタック変数、その他の非ローカル メモリを指すポインターも検出します。  
  
```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  
  
### <a name="checking-a-memory-block"></a>メモリ ブロックのチェック  
 次の例で[_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock)にメモリ ブロックがローカル ヒープ内が有効なブロック型を持つことを確認します。  
  
```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  
  
 [このトピックの内容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_MFC_assertions"></a>MFC アサーション  
 MFC の定義、 [ASSERT](http://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)マクロ アサーションをチェックするためです。 また、`MFC ASSERT_VALID` 派生オブジェクトの内部状態を検証するための `CObject::AssertValid` および `CObject` も定義されています。  
  
 MFC の `ASSERT` マクロの引数がゼロまたは false に評価された場合、マクロはプログラムの実行を停止し、ユーザーに警告を表示します。それ以外の場合、プログラムの実行を続けます。  
  
 アサーションが失敗すると、アサーション対象のソース ファイル名と行番号がメッセージ ダイアログ ボックスに表示されます。 ダイアログ ボックスで [再試行] を選択する場合のボックスへの呼び出し[AfxDebugBreak](http://msdn.microsoft.com/Library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30)デバッガーにブレークを実行します。 この時点で、呼び出し履歴を調べるかその他のデバッガー機能を使って、アサーションが失敗した原因を確認できます。 有効にした場合[ジャスト イン タイムのデバッグ](../debugger/just-in-time-debugging-in-visual-studio.md)デバッガーが既に実行されていないと、ダイアログ ボックスは、デバッガーを起動できます。  
  
 `ASSERT` を使用して関数の戻り値をチェックする方法を次に示します。  
  
```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  
  
 アサートを使用することができます、 [IsKindOf](/cpp/mfc/reference/cobject-class.md#CObject__IsKindOf)関数の引数の型チェックを提供する関数。  
  
```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  
  
 `ASSERT` マクロは、リリース バージョンではコードを生成しません。 リリース バージョンで式を評価する必要がある場合、[を確認してください](http://msdn.microsoft.com/Library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96)ASSERT の代わりにマクロです。  
  
###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a>MFC ASSERT_VALID と cobject::assertvalid  
 [Cobject::assertvalid](/cpp/mfc/reference/cobject-class.md#CObject__AssertValid)メソッドは実行時にオブジェクトの内部状態のチェックを提供します。 `AssertValid` からクラスを派生させる場合、必ずしも `CObject` をオーバーライドする必要はありませんが、そうすることによって、クラスの信頼性を高めることができます。 `AssertValid` によって、オブジェクトのすべてのメンバー変数に対し、有効な値を保持しているかどうかを検証するアサーションが実行されます。 たとえば、ポインターのメンバー変数が NULL でないかどうかをチェックできます。  
  
 `AssertValid` 関数の宣言方法を次に示します。  
  
```  
class CPerson : public CObject  
{  
protected:  
    CString m_strName;  
    float   m_salary;  
public:  
#ifdef _DEBUG  
    // Override  
    virtual void AssertValid() const;  
#endif  
    // ...  
};  
  
```  
  
 `AssertValid` をオーバーライドするときは、派生クラス独自のチェックを行う前に、基底クラスの `AssertValid` を呼び出します。 その後で、ASSERT マクロを使用して、派生クラス独自のメンバーをチェックします。次に例を示します。  
  
```  
#ifdef _DEBUG  
void CPerson::AssertValid() const  
{  
    // Call inherited AssertValid first.  
    CObject::AssertValid();  
  
    // Check CPerson members...  
    // Must have a name.  
    ASSERT( !m_strName.IsEmpty());  
    // Must have an income.  
    ASSERT( m_salary > 0 );  
}  
#endif  
  
```  
  
 オブジェクトを格納しているメンバー変数がある場合は、`ASSERT_VALID` マクロを使用して、そのオブジェクトの内部状態が有効かどうかを検証します (オブジェクトのクラスが `AssertValid` をオーバーライドしている場合)。  
  
 たとえば、クラス`CMyData`、格納されている、 [CObList](/cpp/mfc/reference/coblist-class)メンバー変数のいずれかでします。 `CObList` 型の変数 `m_DataList` は、`CPerson` オブジェクトのコレクションを格納します。 `CMyData` クラスの宣言の概要を次に示します。  
  
```  
class CMyData : public CObject  
{  
    // Constructor and other members ...  
    protected:  
        CObList* m_pDataList;  
    // Other declarations ...  
    public:  
#ifdef _DEBUG  
        // Override:  
        virtual void AssertValid( ) const;  
#endif  
    // And so on ...  
};  
  
```  
  
 `AssertValid` クラスでオーバーライドした `CMyData` は次のようになります。  
  
```  
#ifdef _DEBUG  
void CMyData::AssertValid( ) const  
{  
    // Call inherited AssertValid.  
    CObject::AssertValid( );  
    // Check validity of CMyData members.  
    ASSERT_VALID( m_pDataList );  
    // ...  
}  
#endif  
  
```  
  
 `CMyData` クラスは、`AssertValid` の機構を使用して、データ メンバーに格納されているオブジェクトの有効性を検証します。 `AssertValid` クラスでオーバーライドした `CMyData` は、独自の m_pDataList メンバー変数に対して `ASSERT_VALID` マクロを呼び出します。  
  
 `CObList` クラスも `AssertValid` をオーバーライドしているため、有効性の検証はこの段階では停止しません。 このオーバーライドにより、そのクラスが表すリストの内部状態の有効性も検証されます。 つまり、`CMyData` オブジェクトの有効性を検証すると、そのメンバー変数に格納されている `CObList` リスト オブジェクトの内部状態の有効性も検証されることになります。  
  
 さらにコードを追加すると、リストに格納されている `CPerson` オブジェクトの有効性も検証できます。 たとえば、`CPersonList` から派生クラス `CObList` を生成し、`AssertValid` をオーバーライドできます。 このオーバーライドでは、`CObject::AssertValid` を呼び出した後、リストに格納されている `AssertValid` オブジェクトごとに `CPerson` を呼び出すことによってリストを反復処理します。 `CPerson` クラスは、このトピックの冒頭に示したように、既に `AssertValid` をオーバーライドしています。  
  
 これらの関数やマクロは、デバッグ バージョンのビルドに強力な機構を提供します。 リリース バージョンのビルド時には、この機構は自動的にオフになります。  
  
###  <a name="BKMK_Limitations_of_AssertValid"></a>AssertValid に関する制限事項  
 この関数は、オブジェクトが不正な場合に、アサートしてプログラムの実行を停止します。 ただし、アサートされない場合でも、問題が検出されなかったことを示すだけで、必ずしもオブジェクトに問題がないと保証されたわけではありません。  
  
 [このトピックの内容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Using_assertions"></a>アサーションの使用  
  
###  <a name="BKMK_Catching_logic_errors"></a>論理エラーの検出  
 プログラムの論理に従えば true になるはずの条件にアサーションを設定しておきます。 論理エラーが発生しない場合、このアサーションは特に機能しません。  
  
 たとえば、容器内の気体分子をシミュレートすると想定し、変数 `numMols` で分子の総数を表すことにします。 この数値が 0 より小さくなることはあり得ないため、次のような MFC アサート ステートメントを挿入しておきます。  
  
```  
ASSERT(numMols >= 0);  
  
```  
  
 または、次のように CRT アサーションを挿入することもできます。  
  
```  
_ASSERT(numMols >= 0);  
```  
  
 プログラムが正しく動作していれば、これらのステートメントは何の処理も行いません。 論理エラーが発生した場合`numMols`0 より小さくする、ただし、アサーション、プログラムの実行を停止してが表示されます、[アサートに失敗しました ダイアログ ボックス](../debugger/assertion-failed-dialog-box.md)です。  
  
 [このトピックの内容](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Checking_results_"></a>結果を確認します。  
 アサーションは、ざっと見ただけでは結果がわかりにくい演算をテストする場合に有用です。  
  
 たとえば、次のコードを検討してみます。このコードは、`iMols` の指すリンク リストの内容に基づいて変数 `mols` を更新します。  
  
```  
/* This code assumes that type has overloaded the != operator  
 with const char *   
It also assumes that H2O is somewhere in that linked list.   
Otherwise we'll get an access violation... */  
while (mols->type != "H2O")  
{  
 iMols += mols->num;  
 mols = mols->next;  
}  
ASSERT(iMols<=numMols); // MFC version  
_ASSERT(iMols<=numMols); // CRT version  
```  
  
 `iMols` でカウントされる分子の数は、必ず分子の総数 `numMols` 以下であることが必要です。 このループを目で見ただけでは必ずそうなるかどうかを確認できないため、ループの後にアサート ステートメントを挿入し、その条件が満たされているかどうかをチェックします。  
  
 [このトピックの内容](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Testing_error_conditions_"></a>未処理の検索エラー  
 アサーションを使用すると、コード内のエラー処理が完了しているはずの個所で、エラー条件をチェックできます。 次の例のグラフィック ルーチンは、エラー コードを返します。または、正常終了した場合は 0 を返します。  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* Code to handle errors and  
   reset myErr if successful */  
  
ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  
  
 エラー処理コードが正しく機能していれば、アサート ステートメントに達する前に、発生したエラーは処理され、`myErr` は 0 にリセットされるはずです。 場合`myErr`、別の値、アサーションが失敗した、プログラムが停止され、[アサートに失敗しました ダイアログ ボックス](../debugger/assertion-failed-dialog-box.md)が表示されます。  
  
 ただし、アサート ステートメントは、エラー処理コードに代わるものではありません。 最終リリース バージョンのコードで問題となる可能性のあるアサート ステートメントの例を次に示します。  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* No Code to handle errors */  
  
ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  
  
 このコードは、アサート ステートメントを使用してエラー条件を処理しています。 その結果、`myGraphRoutine` が返すエラー コードは、最終リリース バージョンのコードでは処理されないままになります。  
  
 [このトピックの内容](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>参照  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 [マネージ コードのアサーション](../debugger/assertions-in-managed-code.md)