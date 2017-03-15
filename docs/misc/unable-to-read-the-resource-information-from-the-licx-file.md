---
title: "Unable to read the resource information from the licx file | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.fail_reading_licx_file"
ms.assetid: e59f0965-fa1c-4852-bd39-63430d5b7d9f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to read the resource information from the licx file
プロジェクト システムによって .licx ファイルを読み取ることができませんでした。  プロジェクト システムは、ライセンスを準備する過程で、COM\+ ライセンス モデル用に、テキストの .licx ファイルをバイナリのリソース ファイルに変換します。  
  
 .licx ファイルは、ライセンスされたコントロールがフォームに追加されると、Windows フォーム デザイナーによって自動的に生成または更新されます。  プロジェクトごとに .licx ファイルが 1 つ存在します。このファイルは、ルート フォルダーに常に Licenses.licx という名前で格納されます。  
  
 このエラーにはいくつかの原因があります。  
  
-   アクセス許可が拒否された。  
  
-   Web プロジェクトの Web サーバーとの通信が切断された。  
  
 このエラーが発生した場合、ビルド プロセスは失敗します。  
  
## 参照  
 [方法 : コンポーネントおよびコントロールのライセンス処理を行う](../Topic/How%20to:%20License%20Components%20and%20Controls.md)