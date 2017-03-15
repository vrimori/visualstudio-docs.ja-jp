---
title: "Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.satellite_build_failed"
ms.assetid: c97c589f-cf4d-4f6b-941a-7526a1091fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt;
特定のカルチャ設定のサテライト アセンブリを作成できませんでした。  このエラーが発生すると、ビルド処理が失敗します。  
  
 このエラーは、2 つの原因により発生します。  
  
1.  ALINK.EXE がシステムにインストールされていない。  
  
2.  ALINK.EXE が失敗したが、拡張エラー情報がまったく返されなかった。  
  
 **このエラーを解決するには**  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を再インストールするか、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のみを再インストールします。  
  
-   \<理由\> 欄に "アセンブリ リンカーを起動できませんでした。  ファイルがあります" と出力されている場合は、ファイルが生成される Temp フォルダー \(C:\\Documents and Settings\\\<user\>\\Local Settings\\Temp など\) を空にします。  
  
## 参照  
 [Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)