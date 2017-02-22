---
title: "方法: ツールボックスにアクティビティを追加する (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "アクティビティ, ツールボックスへの追加"
  - "ツールボックス, アクティビティの追加"
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 方法: ツールボックスにアクティビティを追加する (レガシ)
[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]を使用してワークフロー ソリューションを作成する場合に、カスタム アクティビティをワークフロー プロジェクト、および **\[ツールボックス\]** 内に配置されたデザイナーに追加すると、それらのアクティビティに簡単にアクセスできます。また、ダイナミック リンク ライブラリ \(DLL\) から **\[ツールボックス\]** にアクティビティを直接追加することもできます。  
  
### DLL からツールボックスにアクティビティを追加するには  
  
1.  **\[Windows Workflow\]** のツールボックス ウィンドウ領域を右クリックして、**\[アイテムの選択\]** をクリックします。  
  
2.  **\[ツールボックス アイテムの選択\]** ダイアログ ボックスで、**\[System.Activities コンポーネント\]** タブをクリックし、ウィンドウの右下の **\[参照\]** をクリックします。  
  
3.  **\[ツールボックス\]** に追加するカスタム アクティビティの実装が格納されているファイル ディレクトリから DLL を選択して、**\[開く\]** をクリックします。  
  
4.  **\[OK\]** をクリックすると、アクティビティがツールボックスに追加されます。  
  
## 参照  
 [従来のアクティビティ デザイナーの使用](../workflow-designer/using-the-legacy-activity-designer.md)   
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)