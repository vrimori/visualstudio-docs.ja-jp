---
title: "アセンブリ &#39;&lt;filepath1&gt;&#39; は、&#39;&lt;filepath2&gt;&#39; と &#39;&lt;filepath3&gt;&#39; の間であいまいなアセンブリ &#39;&lt;assemblyidentity&gt;&#39; を参照しています | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42205"
  - "bc42205"
helpviewer_keywords: 
  - "BC42205"
ms.assetid: c36feb10-dded-4073-9553-af278ae5560b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# アセンブリ &#39;&lt;filepath1&gt;&#39; は、&#39;&lt;filepath2&gt;&#39; と &#39;&lt;filepath3&gt;&#39; の間であいまいなアセンブリ &#39;&lt;assemblyidentity&gt;&#39; を参照しています
アセンブリ '\<filepath1\>' は、'\<filepath2\>' と '\<filepath3\>' の間であいまいなアセンブリ '\<assemblyidentity\>' を参照しています。 '\<filepath2\>' が使用されます。  
  
 複数のファイルの参照先に指定している別のアセンブリの型にアセンブリがアクセスしています。  
  
 コンパイラは、さまざまな場所にあるファイルが同じアセンブリの同じバージョンを保持することを保証できません。 したがって、ファイル参照があいまいで、コンパイラはいずれかを選択する必要があります。  
  
 *アセンブリ ID* には、アセンブリの名前、バージョン、公開キー \(存在する場合\)、およびカルチャが含まれます。 この情報はアセンブリを一意に識別します。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」をご覧ください。  
  
 **エラー ID:** BC42205  
  
### このエラーを解決するには  
  
1.  どのファイルがアセンブリの最適な選択肢かを決定します。 必要に応じて、最新のバージョン、ファイルのアクセシビリティ、および更新される可能性などの条件を使用する場合があります。  
  
2.  選択したファイルへの同一のファイル パスを使用するように、このアセンブリへのすべてのファイル参照を変更します。  
  
## 参照  
 [ビルドに存在しません: アセンブリ](http://msdn.microsoft.com/ja-jp/6c5c7b30-fa78-4f40-b908-120d0743b0e6)   
 [共通言語ランタイムのアセンブリ](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [アセンブリの利点](../Topic/Assembly%20Benefits.md)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [NIB: 参照の管理](http://msdn.microsoft.com/ja-jp/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)