---
title: "フレンド アセンブリ参照 &lt;reference&gt; は無効です。 InternalsVisibleTo 宣言に、バージョン、カルチャ、公開キー トークン、またはプロセッサ アーキテクチャを指定することはできません。 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31534"
  - "vbc31534"
helpviewer_keywords: 
  - "BC31534"
ms.assetid: ae1e470e-3105-48f2-87b1-466e395a7d44
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# フレンド アセンブリ参照 &lt;reference&gt; は無効です。 InternalsVisibleTo 宣言に、バージョン、カルチャ、公開キー トークン、またはプロセッサ アーキテクチャを指定することはできません。
<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性コンストラクターに渡すアセンブリ名に、`Version`、`Culture`、`PublicKeyToken`、または `processorArchitecture` 属性が含まれています。  
  
 **エラー ID:** BC31534  
  
### このエラーを解決するには  
  
1.  <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性コンストラクターに渡すアセンブリ名から、属性 `Version`、`Culture`、`PublicKeyToken`、または `processorArchitecture` を削除します。  
  
## 参照  
 <xref:System.Reflection.AssemblyName>   
 [ビルド内にありません: フレンド アセンブリ \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/80e7a33a-ca91-450b-a00e-c5a7986e228c)