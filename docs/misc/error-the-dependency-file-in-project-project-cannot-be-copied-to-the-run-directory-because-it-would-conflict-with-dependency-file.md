---
title: "エラー : プロジェクト &#39;project&#39; の依存関係 &#39;file&#39; は、依存関係 &#39;file&#39; と競合するため、実行ディレクトリにコピーできません。 | Microsoft Docs"
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
  - "vs.tasklisterror.copy_version_conflict"
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# エラー : プロジェクト &#39;project&#39; の依存関係 &#39;file&#39; は、依存関係 &#39;file&#39; と競合するため、実行ディレクトリにコピーできません。
参照間で競合が発生しています。アプリケーションが実行される bin ディレクトリに、ファイル名が同じ複数の依存関係がコピーされようとしています。 どの依存関係もプライマリ参照ではないため、実行ディレクトリは競合を解決できません。  
  
 このエラーが発生すると、ビルドが失敗します。  
  
 このタスク一覧の項目をダブルクリックすると、競合が発生しているプロジェクトの参照ノードが表示されます。  
  
 **このエラーを解決するには**  
  
-   アセンブリのいずれかをプロジェクトの直接参照にします。 この方法で考えられる欠点は、選択するアセンブリが、他のバージョンの参照アセンブリを要求するアセンブリと共に動作することが保証されない点です。  
  
     または  
  
-   両方のアセンブリ コピーが厳密に命名され、グローバル アセンブリ キャッシュに存在することを確認します。 これにより、アセンブリを bin ディレクトリにコピーする必要がなくなります。  
  
## 参照  
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [グローバル アセンブリ キャッシュ](../Topic/Global%20Assembly%20Cache.md)   
 [厳密な名前付きアセンブリ](../Topic/Strong-Named%20Assemblies.md)   
 [アセンブリのバージョン管理](../Topic/Assembly%20Versioning.md)   
 [方法 : プロジェクトの依存関係を作成および削除する](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)