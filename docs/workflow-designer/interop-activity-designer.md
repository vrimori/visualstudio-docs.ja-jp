---
title: "Interop アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Interop.UI"
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Interop アクティビティ デザイナー
**Interop** アクティビティ デザイナーは、<xref:System.Activities.Statements.Interop> アクティビティを作成および構成するために使用します。  
  
## Interop アクティビティ  
 <xref:System.Activities.Statements.Interop> アクティビティでは、ワークフロー内の <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> から派生する型の実行を管理します。  
  
### Interop アクティビティ デザイナーの使用  
 **Interop** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[移行\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、**\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツールボックス\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 プロジェクトの対象が完全版の [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] である場合は、**\[ツールボックス\]** に、<xref:System.Activities.Statements.Interop> アクティビティを含む [移行](../workflow-designer/migration-activity-designers.md) カテゴリのみが表示されます。  
  
 C\# プロジェクトの場合、完全版の [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] を使用するようにプロジェクトのターゲットを再指定するには、**ソリューション エクスプローラー**でプロジェクトを右クリックし、**\[プロパティ\]** を選択します。**\[アプリケーション\]** タブの **\[ターゲット フレームワーク\]** で、**\[.NET Framework 4\]** オプションを選択します。この変更の確認を求めるために表示された **\[ターゲット フレームワークの変更\]** ダイアログ ボックスで、**\[はい\]** ボタンをクリックします。  
  
 VB プロジェクトの場合、完全版の [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] を使用するようにプロジェクトのターゲットを再指定するには、**ソリューション エクスプローラー**でプロジェクトを右クリックし、**\[プロパティ\]** を選択します。**\[コンパイル\]** タブで、**\[詳細コンパイル オプション\]** をクリックします。**\[ターゲット フレームワークの一覧\]** で、**\[.Net Framework 4\]** を選択し、**\[OK\]** をクリックします。この変更の確認を求めるために表示された **\[ターゲット フレームワークの変更\]** ダイアログ ボックスで、**\[はい\]** ボタンをクリックします。  
  
 **Interop** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、Interop という既定の **DisplayName** を持つ <xref:System.Activities.Statements.Interop> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> は、**Interop** アクティビティ デザイナーのヘッダーか、プロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
 **Interop** アクティビティ デザイナーまたはプロパティ グリッドで、**\[ActivityType\]** ボックスの **\[クリックして参照\]** というテキストをクリックして、**\[.NET 型の参照と選択\]** ダイアログ ボックスを表示します。ワークフロー 3.0 またはワークフロー 3.5 のアクティビティの型のみ \(つまり、<xref:System.Workflow.ComponentModel.Activity> から派生した型のみ\) が表示されます。このダイアログ ボックスを使用して型を指定する方法[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[\[.NET 型の参照と選択\] ダイアログ ボックス](../Topic/Browse%20and%20Select%20a%20.NET%20Type%20Dialog%20Box.md)」を参照してください。  
  
### Interop のプロパティ  
 次の表に、<xref:System.Activities.Statements.Interop> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドまたは[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.Interop> アクティビティの表示名。既定値は Interop です。表示名は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|必須|<xref:System.Activities.Statements.Interop> アクティビティに含まれているアクティビティの型を指定します。指定されたこの型は、<xref:System.Workflow.ComponentModel.Activity> から派生していることが必要です。|  
  
## 参照  
 [移行](../workflow-designer/migration-activity-designers.md)