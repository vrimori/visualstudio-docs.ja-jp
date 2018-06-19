---
title: ワークフロー デザイナーで Windows Workflow Foundation (レガシ) 用の Visual Studio デバッガーを無効にします。
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 473ee507e35f5ec5df902df64ee34326dcf90a2b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969966"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Visual Studio Debugger for Windows Workflow Foundation の無効化 (レガシ)

このトピックでは、従来の Windows ワークフロー デザイナーでの Windows Workflow Foundation (WF) アプリケーションの構築時に、構成ファイルを使用して Visual Studio デバッガーを無効にする方法について説明します。 .NET Framework version 3.5、または、WinFX を対象とする必要がある場合は、従来のワークフロー デザイナーを使用します。

 既定では、ホスト プロセスに対して、Visual Studio デバッガーの Windows Workflow Foundation (WF) が有効にします。 ワークフローのデバッグを無効にする必要があります明示的にオフにする"disableworkflowdebugging という"エントリを追加して**\<スイッチ >** 内の要素、  **\<system.diagnostics >** ホスト構成ファイルのセクションです。

 次の例は、ワークフローのデバッグを無効化するためにホスト構成ファイルを変更する方法を示します。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>関連項目

- [Visual Studio Debugger for Windows Workflow Foundation の起動 (レガシ)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)