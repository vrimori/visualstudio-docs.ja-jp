---
title: "T4 テキスト テンプレートのディレクティブ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テキスト テンプレート, アセンブリ ディレクティブ"
  - "テキスト テンプレート, ディレクティブ"
  - "テキスト テンプレート, インポート ディレクティブ"
  - "テキスト テンプレート, インクルード ディレクティブ"
  - "テキスト テンプレート, 出力ディレクティブ"
  - "テキスト テンプレート, テンプレート ディレクティブ"
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 81
caps.handback.revision: 81
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 テキスト テンプレートのディレクティブ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ディレクティブは、テキスト テンプレート変換エンジンに対する命令です。  
  
 ディレクティブの構文は次のとおりです。  
  
```  
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>  
```  
  
 属性値はすべて、二重引用符で囲む必要があります。  値そのものに引用符が含まれている場合は、\\ 文字でエスケープする必要があります。  
  
 通常、ディレクティブはテンプレート ファイルまたはインクルード ファイル内の最初の要素となります。  コード ブロック \(`<#...#>`\) 内およびクラス機能ブロック \(`<#+...#>`\) の後に、ディレクティブを配置することはできません。  
  
 [T4 テンプレート ディレクティブ](../modeling/t4-template-directive.md)  
 ```  
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 [T4 パラメーター ディレクティブ](../modeling/t4-parameter-directive.md)  
 ```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 [T4 出力ディレクティブ](../modeling/t4-output-directive.md)  
 ```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 [T4 アセンブリ ディレクティブ](../modeling/t4-assembly-directive.md)  
 ```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 [T4 インポート ディレクティブ](../modeling/t4-import-directive.md)  
 ```  
<#@ import namespace="namespace" #>  
```  
  
 [T4 インクルード ディレクティブ](../modeling/t4-include-directive.md)  
 ```  
<#@ include file="filePath" #>  
```  
  
 [T4 CleanUpBehavior ディレクティブ](../modeling/t4-cleanupbehavior-directive.md)  
 ```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 独自のディレクティブを作成することもできます。  詳細については、「[カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)」を参照してください。  Visualization and Modeling SDK を使用してドメイン固有言語 \(DSL\) を作成すると、DSL の一部としてディレクティブ プロセッサが生成されます。