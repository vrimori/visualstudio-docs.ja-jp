---
title: "プロジェクト &#39;&lt;projectname&gt;&#39; にはアセンブリ &#39;&lt;assemblyname&gt;&#39; のバージョン &#39;&lt;versionnumber1&gt;&#39; への参照が必要ですが、アセンブリ &#39;&lt;assemblyname&gt;&#39; のバージョン &#39;&lt;versionnumber2&gt;&#39; を参照します (Visual Basic 警告) | Microsoft Docs"
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
  - "vbc42203"
  - "bc42203"
helpviewer_keywords: 
  - "BC42203"
ms.assetid: 26a3fa34-ec5d-4817-a947-3959446a924a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# プロジェクト &#39;&lt;projectname&gt;&#39; にはアセンブリ &#39;&lt;assemblyname&gt;&#39; のバージョン &#39;&lt;versionnumber1&gt;&#39; への参照が必要ですが、アセンブリ &#39;&lt;assemblyname&gt;&#39; のバージョン &#39;&lt;versionnumber2&gt;&#39; を参照します (Visual Basic 警告)
プロジェクト '\<projectname\>' にはアセンブリ '\<assemblyname\>' のバージョン '\<versionnumber1\>' への参照が必要ですが、アセンブリ '\<assemblyname\>' のバージョン '\<versionnumber2\>' を参照します。 バージョン '\<versionnumber1\>' への参照が発生しました。  
  
 プロジェクトは、他の場所で定義されているアセンブリへの間接参照を行いますが、プロジェクトでは、それ以前のバージョンのアセンブリへの直接参照も含まれています。  
  
 以前のバージョンは除外し、以降のバージョンで定義されている型およびプログラミング要素へのアクセスに対応するために、アクセスを解決するときに、コンパイラは以降のバージョンへの間接参照を使用します。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42203  
  
### このエラーを解決するには  
  
-   以前のバージョンのアセンブリへの間接参照を削除するか、または以降のバージョンへの参照に変更します。  
  
## 参照  
 [共通言語ランタイムのアセンブリ](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [NIB: 名前空間およびコンポーネントの参照](http://msdn.microsoft.com/ja-jp/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [NIB: 参照の管理](http://msdn.microsoft.com/ja-jp/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)