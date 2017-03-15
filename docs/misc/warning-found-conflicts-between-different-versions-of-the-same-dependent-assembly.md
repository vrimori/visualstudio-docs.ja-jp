---
title: "警告 : 同じ依存アセンブリの異なるバージョン間での競合が見つかりました。 | Microsoft Docs"
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
  - "ResolveAssemblyReference.SuggestedRedirects"
ms.assetid: fd14a789-bbdf-46c7-bcd3-9d3165adf96d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 警告 : 同じ依存アセンブリの異なるバージョン間での競合が見つかりました。
この警告は、プロジェクトの依存グラフに同じアセンブリの別のバージョンへの参照が含まれる場合に表示されます。  
  
 app.config ファイルがある場合は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって、そのファイルへのバインディング リダイレクトを追加できます。  バインディング リダイレクトは、すべてのアセンブリ参照をアセンブリの番号が最も大きいバージョンに強制的にリダイレクトします。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はリダイレクト情報を app.config に保存します。  バインディング リダイレクトを使用すると、この警告は表示されません。  
  
 バインディング リダイレクトを追加しない場合、プロジェクトは以前と同じアセンブリ バージョンを参照します。  ただし、この警告は以降も表示されます。  
  
### このエラーを解決するには  
  
-   警告をダブルクリックし、"app.config ファイルにバインド リダイレクト レコードを追加してこの競合を修正しますか?" というメッセージが表示されたら、\[はい\] をクリックします。