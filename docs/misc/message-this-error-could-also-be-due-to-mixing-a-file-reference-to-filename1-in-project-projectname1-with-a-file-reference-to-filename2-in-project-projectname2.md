---
title: "&lt;message&gt; このエラーは、プロジェクト &#39;&lt;projectname1&gt;&#39; の &#39;&lt;filename1&gt;&#39; へのファイル参照と、プロジェクト &#39;&lt;projectname2&gt;&#39; の &#39;&lt;filename2&gt;&#39; へのファイル参照との混合によって生じた可能性があります | Microsoft Docs"
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
  - "bc30970"
  - "vbc30970"
helpviewer_keywords: 
  - "BC30970"
ms.assetid: 81cc4f7b-cc16-46cc-9a49-74980300e158
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;message&gt; このエラーは、プロジェクト &#39;&lt;projectname1&gt;&#39; の &#39;&lt;filename1&gt;&#39; へのファイル参照と、プロジェクト &#39;&lt;projectname2&gt;&#39; の &#39;&lt;filename2&gt;&#39; へのファイル参照との混合によって生じた可能性があります
\<message\> このエラーは、プロジェクト '\<projectname1\>' の '\<filepathname1\>' へのファイル参照とプロジェクト '\<projectname2\>' の '\<filepathname2\>' へのファイル参照との混合によって生じた可能性があります。  両方のアセンブリが同一である場合は、これらの参照を同じ場所から参照するように置き換えてください。  
  
 プロジェクト内のコードが別のプロジェクトのメンバーにアクセスしていますが、このプロジェクトのソリューションは [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラに参照の解決を許可するよう構成されていません。  
  
 別のアセンブリで定義されている型にアクセスするには、そのアセンブリへの参照を [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラが保持する必要があります。 これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。  
  
 **エラー ID:** BC30970  
  
### このエラーを解決するには  
  
1.  どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。 この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。  
  
2.  プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むファイルへの参照を追加します。  
  
## 参照  
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [NIB: 名前空間およびコンポーネントの参照](http://msdn.microsoft.com/ja-jp/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [NOTINBUILD: 同じ名前を持つ複数の変数がある場合に参照を解決する](http://msdn.microsoft.com/ja-jp/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB 方法: プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [壊れた参照のトラブルシューティング](../ide/troubleshooting-broken-references.md)