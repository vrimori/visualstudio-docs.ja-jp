---
title: List Disassembly コマンド | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3007b5d675ab8e48406fdaaa69c4858554968920
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="list-disassembly-command"></a>ListDisassembly コマンド
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
  
## <a name="see-also"></a>参照  
 [ListCallStack コマンド](../../ide/reference/list-call-stack-command.md)   
 [スレッドの一覧表示コマンド](../../ide/reference/list-threads-command.md)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)