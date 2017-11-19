---
title: "SharePoint プロジェクト システムを拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
ms.assetid: 654b2973-a5c9-44be-a3d2-8bc3d15f9624
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 99380078b2fc49bcc5e1efb7a36ac7f28028a0d7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-sharepoint-project-system"></a>SharePoint プロジェクト システムの拡張
  SharePoint ソリューションを作成するには、Visual Studio でプロジェクト テンプレートと項目テンプレートのセットを使用します。 これらのテンプレートは、多くの開発シナ リオの要件を満たすが必要な機能を提供しない場合を検出する可能性があります。 このような場合は、SharePoint プロジェクト システムを拡張することができます。  
  
## <a name="overview-of-the-sharepoint-project-system"></a>SharePoint プロジェクト システムの概要  
 SharePoint プロジェクト システムはの基本的なコンポーネントに基づいて*SharePoint プロジェクト項目*です。 SharePoint プロジェクト項目では、リスト定義、Web パーツ、コンテンツの種類など、1 つの SharePoint カスタマイズを表します。  
  
 SharePoint プロジェクトは、1 つまたは複数の SharePoint プロジェクト項目を含む Visual Studio プロジェクトです。 SharePoint プロジェクトには、機能と展開のパッケージにプロジェクト項目をグループ化する方法を定義するその他のコンポーネントも含まれます。  
  
 SharePoint プロジェクト項目および SharePoint プロジェクトの内容に関する詳細については、次を参照してください。[項目テンプレートを作成し、SharePoint プロジェクト項目用のプロジェクト テンプレート](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)です。  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>SharePoint プロジェクト システムを拡張する方法  
 SharePoint プロジェクト システムは、次のように拡張できます。  
  
-   独自の SharePoint プロジェクト項目の種類を定義し、新しい項目テンプレート、または Visual Studio でのプロジェクト テンプレートに関連付けます。 たとえば、カスタム アクションまたはフィールドを作成するための SharePoint プロジェクト項目の種類を定義できます。 詳細については、次を参照してください。[カスタム SharePoint プロジェクト項目の種類を定義する](../sharepoint/defining-custom-sharepoint-project-item-types.md)です。  
  
-   Visual Studio で既にインストールされている SharePoint プロジェクト項目の種類を拡張します。 プロジェクト項目でショートカット メニュー項目を追加するなど、**ソリューション エクスプ ローラー**および開発者がメニュー項目を選択すると、プロジェクト項目をカスタマイズします。 詳細については、次を参照してください。 [SharePoint プロジェクト項目の拡張](../sharepoint/extending-sharepoint-project-items.md)です。  
  
-   SharePoint プロジェクトを拡張します。 たとえば、項目を追加または SharePoint プロジェクトから削除されたときに、特定のタスクを実行するイベント ハンドラーを追加することができます。 詳細については、次を参照してください。 [SharePoint プロジェクトの拡張](../sharepoint/extending-sharepoint-projects.md)です。  
  
-   SharePoint プロジェクト項目および SharePoint プロジェクトのパッケージ化と配置の動作を拡張します。 たとえば、追加のカスタム タスクを実行するには、Visual Studio は、特定の展開の手順を実行するとき、または配置時や、プロジェクトの取り消し時に実行する独自の展開ステップを作成できます。 詳細については、次を参照してください。[を拡張する SharePoint のパッケージ化と配置](../sharepoint/extending-sharepoint-packaging-and-deployment.md)です。  
  
## <a name="common-development-tasks"></a>一般的な開発タスク  
 SharePoint プロジェクト システムの拡張機能では、次の一般的なタスクを実行できます。  
  
-   プロジェクト項目とはいくつかの異なる種類のプロジェクト ファイルでは、カスタムの文字列データを保存します。 詳細については、次を参照してください。 [SharePoint プロジェクト システムの拡張機能でのデータの保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)です。  
  
-   SharePoint プロジェクト システムで Visual Studio オートメーション オブジェクト モデルまたは統合オブジェクト モデル内の対応するオブジェクトをオブジェクトに変換またはその逆です。 詳細については、次を参照してください。[間で SharePoint プロジェクト システムの種類の変換およびその他の Visual Studio プロジェクトの種類](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)です。  
  
## <a name="see-also"></a>関連項目  
 [カスタム SharePoint プロジェクト項目の種類を定義します。](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [SharePoint プロジェクト項目の拡張](../sharepoint/extending-sharepoint-project-items.md)   
 [SharePoint プロジェクトの拡張](../sharepoint/extending-sharepoint-projects.md)   
 [SharePoint の拡張のパッケージ化と配置](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [SharePoint プロジェクト システムの拡張機能におけるデータの保存](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [SharePoint プロジェクト システムの種類とその他の Visual Studio プロジェクトの種類間の変換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Visual Studio での SharePoint ツールを拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [SharePoint ツール拡張機能におけるプログラミングに関する概念および特徴](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  