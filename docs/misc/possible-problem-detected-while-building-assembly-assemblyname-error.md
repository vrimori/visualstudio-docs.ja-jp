---
title: "アセンブリ &#39;&lt;assemblyname&gt;&#39; をビルド中に問題が発生した可能性があります: &lt;error&gt; | Microsoft Docs"
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
  - "vbc40010"
  - "bc40010"
helpviewer_keywords: 
  - "BC40010"
ms.assetid: 3a4f4a4a-a5ad-4501-bf4c-0fbf25c50734
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# アセンブリ &#39;&lt;assemblyname&gt;&#39; をビルド中に問題が発生した可能性があります: &lt;error&gt;
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラによって呼び出された ALink ツールが、アセンブリのビルド中にエラーが発生したことを報告しています。 考えられる原因は次のとおりです。  
  
-   署名されたアセンブリが署名されていないアセンブリを参照しています。 この場合、参照されるアセンブリが、セキュリティ基準を満たすかどうかを判断する必要があります。  
  
-   32 ビット プラットフォーム上で 64 ビット アプリケーションを構築しています。 この場合、参照されるすべてのアセンブリの 64 ビット バージョンがターゲット プラットフォームにインストールされていることを確認する必要があります。 共通言語ランタイム \(CLR\) アセンブリでは、これは自動的に処理されますが、このエラー メッセージは生成されます。  
  
 このメッセージは警告です。 コンパイラは、アセンブリの生成を続行しています。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40010  
  
### このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを確認し、適切な処理を行います。  
  
2.  プログラムをもう一度コンパイルし、エラーがまだ発生するかどうか確認します。  
  
3.  エラーがまだ発生する場合は、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラを再インストールします。  
  
4.  再インストール後にエラーが続く場合は、状況に関する情報を収集し、Microsoft 製品サポート サービスに通知してください。  
  
## 参照  
 [PAVEOVER 製品のサポートとアクセシビリティ](http://msdn.microsoft.com/ja-jp/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)   
 [Common Language Runtime Overview](http://msdn.microsoft.com/ja-jp/0fd9aeae-af10-435f-86d4-e76619741e4a)