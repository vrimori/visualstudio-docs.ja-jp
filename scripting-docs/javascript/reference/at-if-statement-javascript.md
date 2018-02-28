---
title: "@ifステートメント (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@if_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- elif statement
- conditional statements, if
- if statement, @if
- else statement
- '@if statement'
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87cfc157ab16b183ccf687fa221393be4ab74757
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="if-statement-javascript"></a>@ifステートメント (JavaScript)
式の値に応じてステートメント グループを条件付きで実行します。  
  
> [!WARNING]
>  条件付きコンパイルは、Internet Explorer 11 標準モードと [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。 条件付きコンパイルは、Internet Explorer 10 標準モードと、それ以前のすべてのバージョンでサポートされています。  
  
## <a name="syntax"></a>構文  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## <a name="parameters"></a>パラメーター  
 *condition1、condition2*  
 省略可能です。 ブール式に強制変換できる式を指定します。  
  
 `text1`  
 省略可能です。 場合に解析するテキスト`condition1`は**true**です。  
  
 `text2`  
 省略可能です。 場合に解析するテキスト`condition1`は**false**と`condition2`は**true**です。  
  
 `text3`  
 省略可能です。 両方を解析するテキストを`condition1`と`condition2`は**false**です。  
  
## <a name="remarks"></a>コメント  
 `@if` ステートメントを作成する際、各句を個別の行に配置する必要はありません。 複数回使用することができます **@elif** 句。 ただし、すべて **@elif** 句は、前にする必要があります、  **@else** 句。  
  
 `@if` ステートメントは、一般にテキスト出力に使用するテキストを複数の候補の中から選択する場合に使用します。  
  
 ASP ページ用に作成されたスクリプト、ASP.NET ページ用に作成されたスクリプト、またはコマンド ライン プログラム用に作成されたスクリプトで条件付きコンパイル変数を使用することは一般的ではありません。 これは、他の方法を使用してコンパイラの機能を決定できるためです。  
  
 Web ページ用のスクリプトを作成するとき、常にコメント内に条件付きコンパイル コードを追加してください。 これにより、条件付きコンパイルをサポートしないホストでこれらのコードが無視されます。  
  
## <a name="example"></a>例  
 次の例では、使用、  **@if...@elif..です。@else...@end** ステートメントです。  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## <a name="requirements"></a>要件  
 Internet Explorer のすべてのバージョンでサポートされていますが、[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。  
  
## <a name="see-also"></a>関連項目  
 [条件付きコンパイル](../../javascript/advanced/conditional-compilation-javascript.md)   
 [条件付きコンパイル変数](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onステートメント](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@set ステートメント](../../javascript/reference/at-set-statement-javascript.md)