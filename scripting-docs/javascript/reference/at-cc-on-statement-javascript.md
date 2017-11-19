---
title: "@cc_onステートメント (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '@cc_on_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, activating
- '@cc_on statement'
- '@set statement'
- '@if statement'
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e993d5bc8302931a5722495da70612e79f7dfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ccon-statement-javascript"></a>@cc_onステートメント (JavaScript)
スクリプトのコメント内での条件付きコンパイルのサポートをアクティブにします。  
  
> [!WARNING]
>  条件付きコンパイルは、Internet Explorer 11 標準モードと [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。 条件付きコンパイルは、Internet Explorer 10 標準モードと、それ以前のすべてのバージョンでサポートされています。  
  
## <a name="syntax"></a>構文  
  
```  
@cc_on   
```  
  
## <a name="remarks"></a>コメント  
 `@cc_on` ステートメントにより、スクリプトのコメント内の条件付きコンパイルが有効になります。  
  
 ASP ページまたは ASP.NET ページ用に作成されたスクリプトや、コマンド ライン プログラム用に作成されたスクリプトでは、コンパイラの機能が他の方法を使用して決定されるため、条件付きコンパイル変数を使用することは一般的ではありません。  
  
 Web ページ用のスクリプトを作成するとき、常にコメント内に条件付きコンパイル コードを配置してください。 これにより、条件付きコンパイルをサポートしないホストでこれらのコードが無視されます。  
  
 条件付きコンパイルをサポートしないブラウザーがスクリプトを有効な構文として受け入れるように、コメントで `@cc_on` ステートメントを使用することを強くお勧めします。  
  
 `@if` ステートメントまたは `@set` ステートメントをコメント外に記述することでも、条件付きコンパイルをアクティブにできます。  
  
## <a name="example"></a>例  
 次の例は、`@cc_on` ステートメントの使用方法を示します。  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on the 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on the 16-bit version of Windows.");  
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
 [@ifステートメント](../../javascript/reference/at-if-statement-javascript.md)   
 [@set ステートメント](../../javascript/reference/at-set-statement-javascript.md)