---
title: "例外のトラブルシューティング : System.Runtime.InteropServices.SafeArrayRankMismatchException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSafeArrayRankMismatch"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "SafeArrayRankMismatchException クラス"
ms.assetid: 6c69355c-8bfd-49bb-acad-b4d7236ae2e7
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Runtime.InteropServices.SafeArrayRankMismatchException
<xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> 例外は、受信した SAFEARRAY のランクがマネージ シグネチャで指定されているランクと一致しない場合にスローされます。  
  
## 関連するヒント  
 **配列に必要な次元数があることを確認します。**  
 セーフ配列のランクと下限はタイプ ライブラリからは判断できないため、ランクは 1 に等しく下限は 0 に等しいと見なされます。 ランクと下限は、[Tlbimp.exe \(タイプ ライブラリ インポーター\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) によって生成されるマネージ シグネチャで定義する必要があります。  
  
## 参照  
 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [配列に対する既定のマーシャリング](../Topic/Default%20Marshaling%20for%20Arrays.md)   
 [配列](/dotnet/visual-basic/programming-guide/language-features/arrays/index)