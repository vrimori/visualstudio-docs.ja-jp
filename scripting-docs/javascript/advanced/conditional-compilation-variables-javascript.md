---
title: 条件付きコンパイル変数 (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, variables
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 900a44dab0ad418cd2899af6423f78016c90fe2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569122"
---
# <a name="conditional-compilation-variables-javascript"></a>条件付きコンパイル変数 (JavaScript)
条件付きコンパイルで使用可能な定義済み変数を次に示します。 変数が **true** ではない場合は定義されていないので、アクセスされると `NaN` として動作します。  
  
> [!WARNING]
>  条件付きコンパイルは、Internet Explorer 11 より前のすべてのバージョンの Internet Explorer でサポートされています。 Internet Explorer 11 標準モード以降と [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリでは、条件付きコンパイルはサポートされていません。  
  
## <a name="variables"></a>変数  
  
|変数|説明|  
|--------------|-----------------|  
|@_win32|Win32 システムで実行されている場合は true です。|  
|@_win16|Win16 システムで実行されている場合は true です。|  
|@_mac|Apple Macintosh システム上で実行されている場合は true です。|  
|@_alpha|DEC Alpha プロセッサ上で実行されている場合は true です。|  
|@_x86|Intel プロセッサ上で実行されている場合は true です。|  
|@_mc680x0|Motorola 680x0 プロセッサ上で実行されている場合は true です。|  
|@_PowerPC|Motorola PowerPC プロセッサ上で実行されている場合は true です。|  
|@_jscript|常に true です。|  
|@_jscript_build|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] スクリプト エンジンのビルド番号が格納されます。|  
|@_jscript_version|major.minor 形式で [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のバージョン番号が格納されます。|