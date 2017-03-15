---
title: "エラー: x64 プロセスの混合モード デバッグは、Microsoft .NET Framework 4 以上を使用している場合にのみサポートされます | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.interop_unsupported_x64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# エラー: x64 プロセスの混合モード デバッグは、Microsoft .NET Framework 4 以上を使用している場合にのみサポートされます
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ネイティブ コードとマネージ コードの混合を 64 プロセスでデバックするには、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Version 4 が必要です。  [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Version 4 より前のバージョンを使用した 64 ビット プロセスの混合モード デバッグはサポートされません。  
  
### このエラーを解決するには  
  
-   次のいずれかの操作を実行します。  
  
    -   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] を Version 4 にアップグレードします。  
  
    -   デバッグのため、32 ビット バージョンのアプリケーションをビルドします。  
  
## 参照  
 [デバイスのリモート ツールのセットアップ](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)