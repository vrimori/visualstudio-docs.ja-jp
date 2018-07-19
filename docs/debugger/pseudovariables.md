---
title: 擬似変数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af106709ca578abeab19c4f474548476efbeea57
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057688"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Visual Studio デバッガーで擬似変数
擬似変数は変数ウィンドウで特定の情報を表示するために使用条件または**クイック ウォッチ**  ダイアログ ボックス。 通常の変数を入力するときと同様に、擬似変数を入力できます。 ただし、擬似変数は変数ではなく、プログラム内の変数名に対応しません。  
  
## <a name="example"></a>例  
 たとえば、ネイティブ コード アプリケーションを記述していて、アプリケーションに割り当てられたハンドル数を確認する場合を考えてみます。 **ウォッチ** ウィンドウで次の擬似変数を入力できます、**名前**列で、次に戻り値に評価を押します。  
  
`$handles`
  
 ネイティブ コードの場合、次の表に示す擬似変数を使用できます。  
  
|擬似変数|関数|  
|--------------------|--------------|  
|`$err`|SetLastError 関数で設定された最後のエラー値を表示します。 表示される値は、本来 GetLastError が返す値を示します。<br /><br /> `$err,hr` を使用すると、この値のデコードされた形式が表示されます。 たとえば、最後のエラーが 3 の場合、`$err,hr` によって `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.` と表示されます。|  
|`$handles`|アプリケーションに割り当てられているハンドル数を表示します。|  
|`$vframe`|現在のスタック フレームのアドレスを表示します。|  
|`$tid`|現在のスレッドのスレッド ID を表示します。|  
|`$env`|文字列ビューアーの環境ブロックを表示します。|  
|`$cmdline`|プログラムを実行したコマンド ライン文字列を表示します。|  
|`$pid`|プロセス ID を表示します。|  
|`$` *registername*<br /><br /> または<br /><br /> `@` *registername*|レジスタの内容を表示します*registername*します。<br /><br /> 通常は、レジスタ名を入力するだけでレジスタの内容を表示できます。 この構文を使用する必要があるのは、レジスタ名で変数名をオーバーロードしている場合だけです。 レジスタ名が現在のスコープ内での変数名と同じであると、デバッガーは、その名前を変数名と解釈します。 ときに`$` *registername*または`@` *registername*が便利です。|  
|`$clk`|クロック周期の時間を表示します。|  
|`$user`|アプリケーションを実行しているアカウントのアカウント情報と共に、構造体を表示します。 セキュリティ上の理由から、パスワード情報は表示されません。|  
|`$exceptionstack`|現在の Windows ランタイムの例外のスタック トレースを表示します。 `$ exceptionstack` UWP アプリでのみ機能します。 `$ exceptionstack` C++ と SEH 例外はサポートされていません|  
|`$ReturnValue`|.NET Framework メソッドの戻り値を表示します。|  
  
 C# と Visual Basic では、次の表に示す擬似変数を使用できます。  
  
|擬似変数|関数|  
|--------------------|--------------|  
|`$exception`|最後の例外に関する情報が表示されます。 例外が発生しなかった場合、`$exception` を評価してエラー メッセージが表示されます。<br /><br /> Visual c# でのみ、例外処理アシスタントを無効に`$exception`が自動的に追加、**ローカル**例外が発生したときにウィンドウ。|  
|`$user`|アプリケーションを実行しているアカウントのアカウント情報と共に、構造体を表示します。 セキュリティ上の理由から、パスワード情報は表示されません。|  
  
 Visual Basic では、次の表に示す擬似変数を使用できます。  
  
|擬似変数|関数|  
|--------------------|--------------|  
|`$delete` または `$$delete`|作成された暗黙的な変数を削除、**イミディ エイト**ウィンドウ。 構文は`$delete,`*変数*または`$delete,`*変数*`.`|  
|`$objectids` または `$listobjectids`|すべてのアクティブ オブジェクト ID を、指定された式の子として表示します。 構文は`$objectid,`*式*または`$listobjectids,`*式*`.`|  
|`$` *N* `#`|等しいオブジェクト ID を持つオブジェクトを表示*N*します。|  
|`$dynamic`|特殊な表示**動的ビュー**を実装するオブジェクトのノード、`IDynamicMetaObjectProvider`します。 インターフェイス。 構文は`$dynamic,`*オブジェクト*します。 この機能は、.NET Framework Version 4 を使用するコードにのみ適用されます。|  
  
## <a name="see-also"></a>関連項目  
 [ウォッチ ウィンドウと [クイック ウォッチ] の Windows](../debugger/watch-and-quickwatch-windows.md)   
 [変数 Windows](../debugger/debugger-windows.md)