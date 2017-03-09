---
title: "Licenses processor error/warning: &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.licx_generator_task"
ms.assetid: 85750198-7bd3-4936-b1eb-954dcc3ff573
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Licenses processor error/warning: &lt;reason&gt;
.licx ファイルの処理中にツールがエラーまたは警告を返した場合、エラー メッセージまたは警告メッセージが表示されます。  ビルド プロセスの一部として、プロジェクト システムは、Licenses.licx ファイルがある場合は、それを [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ライセンス マネージャーによって認識されるバイナリ ファイルに変換します。  この変換は、インプロセス ツールを使用して行われます。  
  
 このようなエラーまたは警告の最も一般的な原因は、不正な .licx ファイルにあります。  .licx ファイルを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部で編集したり、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内でテキスト エディターを使用して編集したりすると、ファイルが壊れる場合があります。  
  
 このファイルは、通常は Windows フォーム デザイナーおよび Web フォーム デザイナーによって管理されます。  
  
### このエラーを解決するには  
  
1.  .licx ファイルの形式を修正します。  
  
     バイナリ ファイルが生成されなかった場合、エラー メッセージが表示され、ビルド プロセスは失敗します。  警告は、単に情報を示すためだけに表示されます。  
  
## 参照  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/ja-jp/f793852c-da06-4d52-a826-65f635844772)