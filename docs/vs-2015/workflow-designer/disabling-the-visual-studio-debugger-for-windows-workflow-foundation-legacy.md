---
title: Windows Workflow Foundation (レガシ) 用の Visual Studio デバッガーを無効にする |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: fab5278c5f0c7385dd767b8994a04124bc40b283
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172212"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Visual Studio Debugger for Windows Workflow Foundation の無効化 (レガシ)
このトピックでは、従来の [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]で [!INCLUDE[wf](../includes/wf-md.md)] アプリケーションをビルドする場合に、構成ファイルを使用して [!INCLUDE[wfd1](../includes/wfd1-md.md)] デバッガーを無効にする方法について説明します。 [!INCLUDE[wfd2](../includes/wfd2-md.md)] または [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]を使用します。  
  
 既定では、[!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for [!INCLUDE[wf](../includes/wf-md.md)] はホスト プロセスに対して有効です。 ワークフローのデバッグを無効にする必要があります明示的にオフにする"disableworkflowdebugging という"エントリを追加して**\<スイッチ >** 内の要素、  **\<system.diagnostics >** ホストの構成ファイルのセクション。  
  
 次の例は、ワークフローのデバッグを無効化するためにホスト構成ファイルを変更する方法を示します。  
  
```  
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
 [Visual Studio Debugger for Windows Workflow Foundation (レガシ) の起動](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)