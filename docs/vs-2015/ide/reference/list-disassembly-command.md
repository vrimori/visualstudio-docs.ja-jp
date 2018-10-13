---
title: List Disassembly コマンド | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4cbdc3ee566135fe86301deefe1e8be8db431f9f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256660"
---
# <a name="list-disassembly-command"></a>ListDisassembly コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
デバッグ プロセスが開始され、エラーの処理方法を指定できるようになります。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## <a name="switches"></a>スイッチ  
 各スイッチは、完全な形式または短い形式を使用して、呼び出すことができます。  
  
 /count: `number`、/c: `number`、/length: `number`、または /l: `number`  
 任意。 表示する命令の数を指定します。 既定値は 8 です。  
  
 /endaddress: `expression` または /e: `expression`  
 任意。 逆アセンブリを停止するアドレスを指定します。  
  
 /codebytes:`yes`&#124;`no`、/bytes:`yes`&#124;`no`、または /b:`yes`&#124;`no`  
 任意。 コード バイトを表示するかどうかを指定します。 既定値は `no`にする必要があります。  
  
 /source:`yes`&#124;`no` または /s:`yes`&#124;`no`  
 任意。 ソース コードを表示するかどうかを指定します。 既定値は `no`にする必要があります。  
  
 /symbolnames:`yes`&#124;`no`、/names:`yes`&#124;`no`、または /n:`yes`&#124;`no`  
 任意。 シンボル名を表示するかどうかを指定します。 既定値は `yes`にする必要があります。  
  
 [/linenumbers:`yes`&#124;`no`]  
 任意。 ソース コードに関連付けられている行番号の表示を有効にします。 /linenumbers スイッチを使用するには、/source スイッチの値が `yes` である必要があります。  
  
## <a name="example"></a>例  
  
```  
>Debug.ListDisassembly  
```  
  
## <a name="see-also"></a>関連項目  
 [ListCallStack コマンド](../../ide/reference/list-call-stack-command.md)   
 [スレッドの一覧表示コマンド](../../ide/reference/list-threads-command.md)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



