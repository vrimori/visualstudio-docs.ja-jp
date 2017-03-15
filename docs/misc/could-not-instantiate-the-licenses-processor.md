---
title: "Could not instantiate the licenses processor | Microsoft Docs"
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
  - "vs.tasklisterror.no_licx_generator"
ms.assetid: 9e95d590-f41f-4cfa-bc73-fadeacfdb879
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not instantiate the licenses processor
.licx ファイルをバイナリのリソースに変換するために使用するツールをインスタンス化できませんでした。  
  
 プロジェクト システムは、コンパイルの過程で、テキストの .licx ファイルを、.NET のコントロール ライセンス サポートを提供するバイナリのリソースに変換します。  バイナリのリソースは、その後、プロジェクト出力に埋め込まれます。  
  
 このエラーが発生した場合、ビルド プロセスは失敗します。  
  
 .licx ファイルは、ライセンスされたコントロールがフォームに追加されると、Windows フォーム デザイナーによって自動的に生成または更新されます。  プロジェクトごとに .licx ファイルが 1 つ存在します。このファイルは、ルート フォルダーに常に Licenses.licx という名前で格納されます。  
  
 **このエラーを解決するには**  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を再インストールします。  
  
## 参照  
 [方法 : コンポーネントおよびコントロールのライセンス処理を行う](../Topic/How%20to:%20License%20Components%20and%20Controls.md)