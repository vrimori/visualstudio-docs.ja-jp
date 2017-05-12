---
title: "ワークフローでのフォームのサポート"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発, ワークフロー"
  - "ワークフロー [Visual Studio での SharePoint 開発]"
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# ワークフローでのフォームのサポート
  ワークフローでは、関連付け、初期化、タスク、および変更という 4 種類のフォームを使用できます。  これらの種類のフォームは、ASPX フォームまたは InfoPath フォームに基づいて作成できます。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] が特定のフォームに対して提供するサポートのレベルは、さまざまな要素によって決まります。それらを表で説明します。  ワークフロー フォーム形式の詳細については MSDN Web サイト [ワークフロー Forms Overview](http://go.microsoft.com/fwlink/?LinkId=185228) で、参照します。  
  
## XML ファクタリング  
 ASPX 関連付けまたは初期化フォームを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ワークフロー プロジェクト項目に追加すると、フォーム名または配置パスが更新されたとき、またはフォームが削除されたときに、関連付けまたは初期化フォームを参照する属性が常に一致するように、ワークフローの Elements.xml ファイル内の XML が [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって自動的にリファクタリングされます。  ただし、ワークフローで他の種類のフォーム \(タスクや変更フォームなど\) を使用した場合、Elements.xml ファイルはリファクタリングされません。  
  
## 新しい Visual Studio ワークフローでのフォームのサポート  
 次の表に、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で作成されたワークフロー内の ASPX フォームまたは InfoPath フォームの異なる種類のフォームに対する [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のサポートを示します。  
  
|フォームの種類|Visual Studio で ASPX フォームを使用して作成されたワークフロー|Visual Studio で InfoPath フォームを使用して作成されたワークフロー|  
|-------------|-----------------------------------------------|---------------------------------------------------|  
|関連付け|-   ASPX 関連付けフォームは、**ワークフロー関連付けフォーム**項目テンプレートを使用してワークフローに追加できます。<br />-   ワークフローの Elements.xml ファイルは、フォームの追加、名前の変更、削除が実行されたとき、またはその配置パスが変更されたときにリファクタリングされます。<br />-   詳細については、「[チュートリアル: 関連付けフォームと開始フォームを持つワークフローの作成](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)」を参照してください。|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] には InfoPath 関連付けフォーム テンプレートはありません。<br />-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] と InfoPath Designer は統合されていません。<br />-   ワークフローの Elements.xml ファイルはリファクタリングされません。|  
|開始|-   ASPX 初期化フォームは、**ワークフロー初期化フォーム**項目テンプレートを使用してワークフローに追加できます。<br />-   ワークフローの Elements.xml ファイルは、フォームの追加、名前の変更、削除が実行されたとき、またはその配置パスが変更されたときにリファクタリングされます。<br />-   詳細については、「[チュートリアル: 関連付けフォームと開始フォームを持つワークフローの作成](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)」を参照してください。|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] には InfoPath 関連付けフォーム テンプレートはありません。<br />-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] と InfoPath Designer は統合されていません。<br />-   ワークフローの Elements.xml ファイルはリファクタリングされません。|  
|タスク|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で使用できる ASPX タスク フォームはありません。  アプリケーション ページを作成し、そのページにコードを追加する必要があります。<br />-   ワークフローの Elements.xml ファイルはリファクタリングされません。<br />-   詳細については、参照します [ワークフロー タスクがフォーム \(SharePoint Foundation\)](http://go.microsoft.com/fwlink/?LinkId=187674)|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] には InfoPath タスク フォーム テンプレートはありません。<br />-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] と InfoPath Designer は統合されていません。<br />-   ワークフローの Elements.xml ファイルはリファクタリングされません。|  
|変更|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で使用できる ASPX 変更フォームはありません。  変更フォームを追加するには、アプリケーション ページを作成し、そのページにコードを追加する必要があります。<br />-   ワークフローの Elements.xml ファイルはリファクタリングされません。  必要に応じて手動で編集する必要があります。<br />-   詳細については、参照します [ワークフローの変更のフォーム \(SharePoint Foundation\)](http://go.microsoft.com/fwlink/?LinkId=187675)|-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] には InfoPath 変更フォーム テンプレートはありません。<br />-   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] と InfoPath Designer は統合されていません。<br />-   ワークフローの Elements.xml ファイルはリファクタリングされません。|  
  
## インポートされた SharePoint 再利用可能ワークフローでのフォームのサポート  
 次の表に、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] にインポートされた再利用可能ワークフロー内の ASPX フォームまたは InfoPath フォームの異なる種類のフォームに対する [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のサポートを示します。  
  
|フォームの種類|SharePoint Designer からインポートされた ASPX フォームを含む再利用可能ワークフロー|SharePoint Designer からインポートされた InfoPath フォームを含む再利用可能ワークフロー|  
|-------------|------------------------------------------------------------|----------------------------------------------------------------|  
|関連付け|-   フォームは、ワークフローの Elements.xml ファイルで参照されます。<br />-   ワークフローの Elements.xml ファイルは、フォームの名前の変更または削除が実行されたとき、またはその配置パスが変更されたときにリファクタリングされます。|-   フォームはインポートされますが、ワークフローの Elements.xml ファイルでは参照されません。<br />-   ワークフローの Elements.xml ファイルはリファクタリングされません。|  
|開始|-   フォームは、ワークフローの Elements.xml ファイル内でワークフローによって参照されます。<br />-   ワークフローの Elements.xml ファイルは、フォームの名前の変更または削除が実行されたとき、またはその配置パスが変更されたときにリファクタリングされます。|-   フォームはインポートされますが、ワークフローの Elements.xml ファイルでは参照されません。<br />-   ワークフローの Elements.xml ファイルはリファクタリングされません。 **Note:**  これを動作させるには、ルールとプロパティを追加して変更する必要があります。|  
|タスク|-   フォームは、ワークフローの Elements.xml ファイルで参照されます。<br />-   ワークフローの Elements.xml ファイルはリファクタリングされません。|-   フォームはインポートされますが、ワークフローの Elements.xml ファイルでは参照されません。<br />-   ワークフローの Elements.xml ファイルはリファクタリングされません。 **Note:**  これを動作させるには、ルールとプロパティを追加して変更する必要があります。|  
|変更|使用できません。  ASPX 変更フォームは SharePoint Designer では作成できません。|使用できません。  InfoPath 変更フォームは SharePoint Designer では作成されません。ただし、組み込みの SharePoint Server ワークフローは別であり、これはワークフローのエクスポート時に .wsp ファイルに含まれません。|  
  
## 参照  
 [チュートリアル: 関連付けフォームと開始フォームを持つワークフローの作成](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [SharePoint ワークフロー ソリューションの作成](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [既存の SharePoint サイトからのアイテムのインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  