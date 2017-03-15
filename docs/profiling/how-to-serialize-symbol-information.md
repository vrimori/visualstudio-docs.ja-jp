---
title: "方法: シンボル情報をシリアル化する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Performance.General"
helpviewer_keywords: 
  - "プロファイリング ツール、シリアル化 (シンボル情報を)"
  - "パフォーマンス ツール、シリアル化 (シンボル情報を)"
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 方法: シンボル情報をシリアル化する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

アプリケーションの分析に必要なシンボルをシリアル化できます。  シリアル化されたシンボルは、.vsp ファイルに追加されます。  シンボル情報を .vsp ファイルに追加することで、第三者が、元のシンボルにアクセスすることなく、パフォーマンス レポートを分析できるようになります。  シンボルがシリアル化されていない場合、インストルメントされた元の .exe ファイルと .pdb ファイルがないと、.vsp ファイルを分析できません。  
  
### シンボル情報を自動的にシリアル化するには  
  
1.  \[ツール\] メニューの \[オプション\] をクリックします。  
  
     **\[オプション\]** ダイアログ ボックスが表示されます。  
  
2.  **\[パフォーマンス ツール\]** をクリックします。  
  
3.  **\[全般設定\]** の **\[シンボル情報を自動的にシリアル化\]** を選択します。  
  
## 参照  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [方法: Windows シンボル情報を参照する](../profiling/how-to-reference-windows-symbol-information.md)   
 [How to: Save Analyzed Report Files](http://msdn.microsoft.com/ja-jp/0340ddde-caf4-48ac-8af3-d15dcdade556)