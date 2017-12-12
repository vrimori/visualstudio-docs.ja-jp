---
title: "List Modules コマンド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 081f57f441da17578735317e2d6f8352cd31d30d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="list-modules-command"></a>List Modules コマンド
現在のプロセスのモジュールが一覧表示されます。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### <a name="parameters"></a>パラメーター  
 /Address:`yes|no`  
 省略可能です。 モジュールのメモリ アドレスを表示するかどうかを指定します。 既定値は `yes`にする必要があります。  
  
 /Name:`yes|no`  
 省略可能です。 モジュールの名前を表示するかどうかを指定します。 既定値は `yes`にする必要があります。  
  
 /Order:`yes|no`  
 省略可能です。 モジュールの順序を表示するかどうかを指定します。 既定値は `no`にする必要があります。  
  
 /Path:`yes|no`  
 省略可能です。 モジュールのパスを表示するかどうかを指定します。 既定値は `yes`にする必要があります。  
  
 /Process:`yes|no`  
 省略可能です。 モジュールのプロセスを表示するかどうかを指定します。 既定値は `no`にする必要があります。  
  
 /SymbolFile:`yes|no`  
 省略可能です。 モジュールのシンボル ファイルを表示するかどうかを指定します。 既定値は `no`にする必要があります。  
  
 /SymbolStatus:`yes|no`  
 省略可能です。 モジュールのシンボル ステータスを表示するかどうかを指定します。 既定値は `yes`にする必要があります。  
  
 /Timestamp:`yes|no`  
 省略可能です。 モジュールのタイムスタンプを表示するかどうかを指定します。 既定値は `no`にする必要があります。  
  
 /Version:`yes|no`  
 省略可能です。 モジュールのバージョンを表示するかどうかを指定します。 既定値は `no`にする必要があります。  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 次の例では、現在のプロセスのモジュール名、アドレス、およびタイムスタンプを一覧表示します。  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [方法 : [モジュール] ウィンドウを使用する](../../debugger/how-to-use-the-modules-window.md)