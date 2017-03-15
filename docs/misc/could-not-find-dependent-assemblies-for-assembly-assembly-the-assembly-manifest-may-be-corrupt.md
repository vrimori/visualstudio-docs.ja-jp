---
title: "アセンブリ &#39;assembly&#39; の依存アセンブリが見つかりませんでした。 アセンブリ マニフェストが壊れている可能性があります。 | Microsoft Docs"
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
  - "vs.tasklisterror.cannotfinddependencies"
ms.assetid: 6d6e6dda-6cec-49d0-9659-63dfdbd7d247
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# アセンブリ &#39;assembly&#39; の依存アセンブリが見つかりませんでした。 アセンブリ マニフェストが壊れている可能性があります。
プロジェクト システムが、プロジェクトによって参照されるアセンブリを読み取ることができませんでした。そのため、プロジェクト システムは、アセンブリ依存関係を判断できません。 このエラーがプロジェクトのビルドを妨げることはありません。 ただし、実行時エラーが発生する場合があります。  
  
 **このエラーを解決するには**  
  
-   アセンブリが [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] または [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] に組み込まれていた場合は、Visual Studio を再インストールします。  
  
     または  
  
-   適切なサード パーティ製コントロールを再インストールします。  
  
## 参照  
 [壊れた参照のトラブルシューティング](../ide/troubleshooting-broken-references.md)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/ja-jp/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)