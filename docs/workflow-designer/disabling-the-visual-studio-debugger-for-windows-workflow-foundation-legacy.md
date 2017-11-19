---
title: "Windows Workflow Foundation (レガシ) 用の Visual Studio デバッガーの無効化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 835ca509c86a9be27486ee257839c4e161221e4e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Visual Studio Debugger for Windows Workflow Foundation の無効化 (レガシ)
このトピックでは、従来の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]で [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションをビルドする場合に、構成ファイルを使用して [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] デバッガーを無効にする方法について説明します。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。  
  
 既定では、[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] はホスト プロセスに対して有効です。 ワークフローのデバッグを無効にする必要があります明示的にオフにする"disableworkflowdebugging という"エントリを追加して**\<スイッチ >**内の要素、  **\<system.diagnostics >**ホスト構成ファイルのセクションです。  
  
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
 [Windows Workflow Foundation (レガシ) 用の Visual Studio デバッガーを起動](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)