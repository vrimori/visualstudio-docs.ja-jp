---
title: "Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_write_gen_output"
ms.assetid: eafcee9e-186b-4019-9042-8d8f9fc0925a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt;
プロジェクト システムがカスタム ツールの出力を特定のファイルに書き込むことができませんでした。  
  
 カスタム ツールの入力ファイル名に変更がない場合、カスタム ツールからの出力は同じファイルに書き込まれます。  このエラーは、生成された出力がディスク上でロックされている場合に発生します。  
  
 **このエラーを解決するには**  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を再起動し、カスタム ツールを再度実行します。影響を受けたファイルを右クリックし、ショートカット メニューの **\[カスタム ツールの実行\]** を選択します。  
  
     多くの場合、生成されたファイルは、プロジェクト システムによって更新されていないため無効になります。