---
title: 再利用可能なワークフローをインポートするためのガイドライン |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e88a8549700158a677b019424df5736cb9cc3a55
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767320"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>再利用可能なワークフローをインポートするためのガイドライン
  SharePoint Designer で作成された再利用可能なワークフローをインポートするには、再利用可能な SharePoint 2010 ワークフローのインポート プロジェクト テンプレートを使用[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 このテンプレートをインポート、*宣言**ワークフロー* ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-のみ) に変換します、*コード ワークフロー*、いずれかで強化するため、ワークフローであります。[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]または[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]コード。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [チュートリアル: SharePoint Designer の再利用可能なワークフローの Visual Studio へのインポート](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)です。  
  
 ただし、再利用可能な SharePoint 2010 ワークフローのインポート テンプレートは、ファーム ソリューションのみをインポートすることができます。 サンド ボックス ソリューションとして、ワークフローを展開する場合は、SharePoint 2010 ソリューション パッケージのインポート テンプレートを使用してインポートします。 ただし、これにより、ワークフローをコードに変換できないし、ように変更することはできません。  
  
## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>再利用可能なワークフローのインポート テンプレートを使用して、再利用可能なワークフローをインポートします。
 SharePoint の再利用可能な 2010 ワークフローのインポート テンプレートを使用して再利用可能なワークフローをインポートする場合は、実行またはと同じように、他のソリューションを変更[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint ソリューションがいくつかのアイテムを手動で修正する必要があります。  
  
### <a name="import-task-forms"></a>タスク フォームをインポートします。
 再利用可能な SharePoint 2010 ワークフローのインポート プロジェクト テンプレートはすべての開始との関連付けフォームをインポートしますが、コード ワークフローのスキーマには、1 つのタスク フォームだけで許可されるため、1 つだけタスク フォームをインポートします。 元のワークフロー ソリューションから他のタスク フォームが入れられます、**インポートされたファイルの他の**フォルダー**ソリューション エクスプ ローラー**です。  
  
## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>SharePoint 2010 ソリューション パッケージのインポート テンプレートを使用して再利用可能なワークフローをインポートします。
 SharePoint 2010 ソリューション パッケージのインポート テンプレートを使用して再利用可能なワークフローをインポートする場合は、次の点を考慮する必要があります。  
  
-   ワークフローをインポートすると、すぐに展開できで実行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を選択して、 **f5 キーを押して**キー。 ただし、インポートしたソリューション内のワークフローの任意のものを変更すると、展開して、ワークフローを実行する前に、プロジェクト内の要素を手動で修正するがあります。  
  
-   ワークフローは、宣言型であるためにコードを追加できません。 コード ワークフローにワークフローを変換する必要がありますにインポートする[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]再利用可能な SharePoint 2010 ワークフローのインポート テンプレートを使用しています。  
  
-   デザイン ビューで、ワークフロー デザイナー (.xoml) ファイルを編集できますが、お勧めソース ビューで、編集、ワークフロー デザイナーには、偽のエラーが表示されるためです。  
  
-   ワークフローでのデバッグは、宣言型のコンテンツに対しては機能しません。 ブレークポイントを設定、[!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)]はヒットしません。  
  
## <a name="import-globally-reusable-workflow-solutions"></a>グローバルに再利用可能なワークフロー ソリューションのインポート
 再利用可能な SharePoint 2010 のワークフローのインポート テンプレートを使用してグローバルに再利用可能なワークフローをインポートすることはできません。 グローバルに再利用可能なワークフローをインポートするには、非グローバルに再利用可能なワークフローに変換する必要があるか、SharePoint 2010 ソリューション パッケージのインポート テンプレートを使用する必要があります。  
  
 ワークフローに変換するには、SharePoint Designer でグローバルに再利用可能なワークフローのコピーを作成 (ワークフローのショートカット メニューを開き、を選択して**コピーとして保存**)。 SharePoint の再利用可能な 2010 ワークフローのインポート テンプレートで新しい再利用可能なワークフローをインポート[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
 変更せず、グローバルに再利用可能なワークフローをインポートするには、SharePoint 2010 ソリューション パッケージのインポート テンプレートを使用します。 このメソッドを使用する場合、ワークフローはコード ワークフローには変換されないと、宣言型ワークフローのままです。  
  
## <a name="see-also"></a>関連項目
 [既存の SharePoint サイトからアイテムをインポートします。](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [チュートリアル: SharePoint Designer の再利用可能なワークフローの Visual Studio へのインポート](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  
