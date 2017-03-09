---
title: "A failure occurred writing to the licenses file | Microsoft Docs"
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
  - "vs.tasklisterror.fail_writing_licenses_file"
ms.assetid: 7ea1e2ac-fc94-4d53-8ce9-2ae31bcba85d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# A failure occurred writing to the licenses file
プロジェクト システムによって、変換されたファイルを書き込むことができませんでした。  プロジェクト システムは、ライセンスを準備する過程で、テキストの .licx ファイルを [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ライセンス システムが解釈できるバイナリのライセンス ファイルに変換します。  
  
 このエラーの原因としては、デバイスにディスク領域がないか、ファイル名が MAX\_PATH の制限を超えていることが考えられます。  
  
 **このエラーを解決するには**  
  
-   絶対パスの名前を短くするか、出力ファイルの名前を短くして、プロジェクトを異なるフォルダーに移動します。  
  
     このエラーが発生した場合、ビルド プロセスは失敗します。  
  
## 参照  
 [方法 : コンポーネントおよびコントロールのライセンス処理を行う](../Topic/How%20to:%20License%20Components%20and%20Controls.md)