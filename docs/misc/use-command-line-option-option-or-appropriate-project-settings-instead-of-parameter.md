---
title: "コマンド ライン オプション &#39;&lt;option&gt;&#39; を使用するか、&#39;&lt;parameter&gt;&#39; 以外の適切なプロジェクト設定を使用してください | Microsoft Docs"
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
  - "bc41008"
  - "vbc41008"
helpviewer_keywords: 
  - "BC41008"
ms.assetid: 1c5d6d7a-b767-4dae-aa61-d7fa81d5aad1
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# コマンド ライン オプション &#39;&lt;option&gt;&#39; を使用するか、&#39;&lt;parameter&gt;&#39; 以外の適切なプロジェクト設定を使用してください
アセンブリの公開キー、アセンブリの公開キー コンテナー、または部分署名のアセンブリを含むファイルを指定する好ましい方法は、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラ オプションを使用することです。 コード内で <xref:System.Reflection.AssemblyKeyFileAttribute>、<xref:System.Reflection.AssemblyKeyNameAttribute>、または <xref:System.Reflection.AssemblyDelaySignAttribute> 属性を使用することはお勧めしません。  
  
 **エラー ID:** BC41008  
  
### このエラーを解決するには  
  
1.  コード内で、<xref:System.Reflection.AssemblyKeyFileAttribute>、<xref:System.Reflection.AssemblyKeyNameAttribute>、または <xref:System.Reflection.AssemblyDelaySignAttribute> 属性の代わりに、[\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)、[\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer)、または [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラ オプションを使用します。  
  
## 参照  
 [方法: 署名されたフレンド アセンブリを作成する](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)   
 [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer)   
 [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign)