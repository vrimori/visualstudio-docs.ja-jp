---
title: "擬似変数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッグ [Visual Studio], 擬似変数"
  - "擬似変数"
  - "[ウォッチ] ウィンドウ, 擬似変数"
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 擬似変数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

擬似変数は、変数ウィンドウまたは **\[クイック ウォッチ\]** ダイアログ ボックスに特定の情報を表示するときに使用される用語です。  通常の変数を入力するときと同様に、擬似変数を入力できます。  ただし、擬似変数は変数ではなく、プログラム内の変数名に対応しません。  
  
## 使用例  
 たとえば、ネイティブ コード アプリケーションを記述していて、アプリケーションに割り当てられたハンドル数を確認する場合を考えてみます。  この場合、**\[ウォッチ\]** ウィンドウの **\[名前\]** 列に次の擬似変数を入力し、Enter キーを押すと、擬似変数が評価されます。  
  
```  
$handles  
```  
  
 ネイティブ コードの場合、次の表に示す擬似変数を使用できます。  
  
|擬似変数|関数|  
|----------|--------|  
|`$err`|SetLastError 関数で設定された最後のエラー値を表示します。  表示される値は、本来 GetLastError が返す値を示します。<br /><br /> `$err,hr` を使用すると、この値のデコードされた形式が表示されます。  たとえば、最後のエラーが 3 の場合、`$err,hr` によって `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.` と表示されます。|  
|`$handles`|アプリケーションに割り当てられているハンドル数を表示します。|  
|`$vframe`|現在のスタック フレームのアドレスを表示します。|  
|`$tid`|現在のスレッドのスレッド ID を表示します。|  
|`$env`|文字列ビューアーの環境ブロックを表示します。|  
|`$cmdline`|プログラムを実行したコマンド ライン文字列を表示します。|  
|`$pid`|プロセス ID を表示します。|  
|`$` *registername*<br /><br /> または<br /><br /> `@` *registername*|名前が *registername* のレジスタの内容を表示します。<br /><br /> 通常は、レジスタ名を入力するだけでレジスタの内容を表示できます。  この構文を使用する必要があるのは、レジスタ名で変数名をオーバーロードしている場合だけです。  レジスタ名が現在のスコープ内での変数名と同じであると、デバッガーは、その名前を変数名と解釈します。  このようなときには、`$`*registername* や `@`*registername* が便利です。|  
|`$clk`|クロック周期の時間を表示します。|  
|`$user`|アプリケーションを実行しているアカウントのアカウント情報と共に、構造体を表示します。  セキュリティ上の理由から、パスワード情報は表示されません。|  
|`$exceptionstack`|現在の Windows ランタイムの例外のスタック トレースを表示します。  `$ exceptionstack` は、Windows 8.1 以降で実行されているストア アプリでのみ機能します。  `$ exceptionstack` は、C\+\+ および SHE の例外ではサポートされません。|  
|`$ReturnValue`|.NET Framework メソッドの戻り値を表示します。  「[メソッド呼び出しの戻り値の調査](../Topic/Examine%20return%20values%20of%20method%20calls.md)」を参照してください。|  
  
 C\# と Visual Basic では、次の表に示す擬似変数を使用できます。  
  
|擬似変数|関数|  
|----------|--------|  
|`$exception`|最後の例外に関する情報が表示されます。  例外が発生しなかった場合、`$exception` を評価してエラー メッセージが表示されます。<br /><br /> Visual C\# のみに該当することとして、Exception Assistant が無効なときに例外が発生すると、`$exception` が自動的に **\[ローカル\]** ウィンドウに追加されることが挙げられます。|  
|`$user`|アプリケーションを実行しているアカウントのアカウント情報と共に、構造体を表示します。  セキュリティ上の理由から、パスワード情報は表示されません。|  
  
 Visual Basic では、次の表に示す擬似変数を使用できます。  
  
|擬似変数|関数|  
|----------|--------|  
|`$delete` または`$$delete`|**イミディエイト** ウィンドウで作成された暗黙的な変数を削除します。  構文は、`$delete,` *変数* または `$delete,` *変数*`.` です。|  
|`$objectids` または`$listobjectids`|すべてのアクティブ オブジェクト ID を、指定された式の子として表示します。  構文は、`$objectid,` *式* または `$listobjectids,` *式*`.` です。|  
|`$` *N* `#`|*N* と等しいオブジェクト ID を持つオブジェクトを表示します。|  
|`$dynamic`|`IDynamicMetaObjectProvider` を実装するオブジェクト用の特別な **\[動的ビュー\]** ノードを表示します。  インターフェイス。  構文は `$dynamic,` *オブジェクト* です。  この機能は、.NET Framework Version 4 を使用するコードにのみ適用されます。  「[動的ビュー](../Topic/Dynamic%20View.md)」を参照してください。|  
  
## 参照  
 [ウォッチ ウィンドウと \[クイック ウォッチ\] ウィンドウ](../Topic/Watch%20and%20QuickWatch%20Windows.md)   
 [ウィンドウ](../Topic/Variable%20Windows.md)