---
title: "アセンブリをビルド中に問題が発生した可能性があります: &lt;error&gt; | Microsoft Docs"
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
  - "vbc40009"
  - "bc40009"
helpviewer_keywords: 
  - "BC40009"
ms.assetid: 4bc5108a-a96e-43be-8bba-a47441a25f3e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# アセンブリをビルド中に問題が発生した可能性があります: &lt;error&gt;
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラによって呼び出された ALink ツールが、アセンブリのビルド中にエラーが発生したことを報告しています。 考えられる原因の 1 つに、署名されたアセンブリが署名されていないアセンブリを参照していることがあります。  
  
 このメッセージは警告です。 コンパイラは、アセンブリの生成を続行しています。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40009  
  
### このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを確認し、適切な処理を行います。  
  
2.  プログラムをもう一度コンパイルし、エラーがまだ発生するかどうか確認します。  
  
3.  エラーがまだ発生する場合は、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラを再インストールします。  
  
4.  再インストール後にエラーが続く場合は、状況に関する情報を収集し、Microsoft 製品サポート サービスに通知してください。  
  
## 参照  
 [PAVEOVER 製品のサポートとアクセシビリティ](http://msdn.microsoft.com/ja-jp/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)