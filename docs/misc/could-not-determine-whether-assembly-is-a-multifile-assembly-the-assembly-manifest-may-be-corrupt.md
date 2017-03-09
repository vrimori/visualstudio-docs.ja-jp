---
title: "&#39;assembly&#39; がマルチ ファイル アセンブリかどうかを確認できませんでした。 アセンブリ マニフェストが壊れている可能性があります。 | Microsoft Docs"
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
  - "vs.tasklisterror.cannotfindscatterinfo"
ms.assetid: 2d4af6ef-c2f8-4764-af8b-580d433bfbc9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &#39;assembly&#39; がマルチ ファイル アセンブリかどうかを確認できませんでした。 アセンブリ マニフェストが壊れている可能性があります。
プロジェクト システムはプロジェクトによって参照されるアセンブリを読み取ることができませんでした。このため、プロジェクト システムはどのファイルがアセンブリにより参照されているかを確認できません。  
  
 **このエラーを解決するには**  
  
-   アセンブリが [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] または [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] に組み込まれていた場合は、Visual Studio を再インストールします。  
  
     または  
  
-   適切なサード パーティ製コントロールを再インストールします。  
  
     このエラーがプロジェクトのビルドを妨げることはありません。 ただし、実行時エラーが発生する場合があります。  
  
## 参照  
 [壊れた参照のトラブルシューティング](../ide/troubleshooting-broken-references.md)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/ja-jp/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)