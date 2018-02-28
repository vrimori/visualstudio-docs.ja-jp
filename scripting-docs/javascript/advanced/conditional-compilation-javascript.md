---
title: "条件付きコンパイル (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ConditionalComp_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, overview
- conditional compilation
ms.assetid: a843de4e-3aae-43cd-ad64-477dd00814a2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d6a5987b21afcab8c62a609dfba33f963d544de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-compilation-javascript"></a>条件付きコンパイル (JavaScript)
条件付きコンパイルを使用すると、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の新しい言語機能を利用しながら、その機能をサポートしていない以前のバージョンとの互換性も維持できます。  
  
> [!WARNING]
>  条件付きコンパイルは、Internet Explorer 11 より前のすべてのバージョンの Internet Explorer でサポートされています。 Internet Explorer 11 標準モード以降と [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリでは、条件付きコンパイルはサポートされていません。  
  
## <a name="statements"></a>ステートメント  
 条件付きコンパイルは `@cc_on` ステートメントを使用するか、または `@if` ステートメントまたは `@set` ステートメントを使用してアクティブにします。 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の新機能を使用する場合、スクリプトにデバッグ サポートを埋め込む場合、コード実行をトレースする場合などは、条件付きコンパイルを使用するのが一般的です。  
  
 条件付きコンパイルをサポートできない Netscape Navigator などのホストが無視できるように、条件付きコンパイルのコードは必ずコメント内に配置します。 次に例を示します。  
  
```JavaScript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
 この例では、`@cc_on` ステートメントによって条件付きコンパイルがアクティブにされた場合にだけ使用される、特殊なコメント区切り文字を使用しています。 条件付きコンパイルをサポートしないスクリプト エンジンでは、条件付きコンパイルがサポートされていないというメッセージのみが表示されます。