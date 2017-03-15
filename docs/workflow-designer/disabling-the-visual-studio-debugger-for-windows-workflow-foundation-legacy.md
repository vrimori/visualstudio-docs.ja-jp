---
title: "Visual Studio Debugger for Windows Workflow Foundation の無効化 (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ワークフローのデバッグ, デバッガーの無効化"
  - "ワークフロー デバッガー, 無効化"
  - "ワークフロー, デバッガーの無効化"
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Visual Studio Debugger for Windows Workflow Foundation の無効化 (レガシ)
このトピックでは、従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]で [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションをビルドする場合に、構成ファイルを使用して [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガーを無効にする方法について説明します。[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]を使用します。  
  
 既定では、[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] はホスト プロセスに対して有効です。ワークフローのデバッグを無効にするには、ホスト構成ファイルの **\<system.diagnostics\>** セクションにある **\<switches\>** 要素に "DisableWorkflowDebugging" というエントリを追加することによって明示的に無効化する必要があります。  
  
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
  
## 参照  
 [Visual Studio Debugger for Windows Workflow Foundation の起動 \(レガシ\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)