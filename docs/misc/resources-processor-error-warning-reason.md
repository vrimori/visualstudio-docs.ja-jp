---
title: "Resources processor error/warning: &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.resx_generator_task"
ms.assetid: eb9a1bd0-7e63-4a2b-ad37-54f6e67d9b5a
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resources processor error/warning: &lt;reason&gt;
.resx ファイルの処理中にツールがエラーまたは警告を返した場合、エラー メッセージまたは警告メッセージが表示されます。  ビルド プロセスの一部として、プロジェクト システムは、各 .resx ファイルを [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] リソース マネージャーによって認識されるバイナリ ファイルに変換します。  この変換は、インプロセス ツールを使用して行われます。  
  
 このようなエラーまたは警告の最も一般的な原因は、不正な .resx ファイルにあります。  .resx ファイルを Visual Studio の外部で編集したり、Visual Studio 内でテキスト エディターを使用して編集したりすると、ファイルが壊れる場合があります。  
  
 このファイルは、通常は Windows フォーム デザイナーおよび Web フォーム デザイナーによって管理されます。  
  
### このエラーを解決するには  
  
1.  .resx ファイルの形式を修正します。  
  
     バイナリ ファイルが生成されなかった場合、エラー メッセージが表示され、ビルド プロセスは失敗します。  警告は、単に情報を示すためだけに表示されます。  
  
## 参照  
 [Resources in .Resx File Format](http://msdn.microsoft.com/ja-jp/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)