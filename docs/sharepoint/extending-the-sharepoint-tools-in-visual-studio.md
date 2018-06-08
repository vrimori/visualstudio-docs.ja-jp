---
title: Visual Studio での SharePoint ツール拡張 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6b63e332ba5cc079ac50f2ef3c4fee84727d95f5
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765337"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Visual Studio での SharePoint ツールを拡張します。
  Visual Studio での SharePoint ツールでは、多くのアプリケーション開発シナ リオの要件を満たしています。 ただし、ここでは提供されませんか、他の開発者が必要とする機能の場合を検出できます。 このような場合は、必要な機能を作成する SharePoint ツールを拡張できます。  
  
## <a name="how-to-extend-the-sharepoint-tools"></a>SharePoint のツールを拡張する方法
 SharePoint プロジェクト システムを拡張して、 **SharePoint 接続**内のノード、**サーバー エクスプ ローラー**ウィンドウです。  
  
### <a name="extend-the-sharepoint-project-system"></a>SharePoint プロジェクト システムを拡張します。
 Visual Studio には、プロジェクト テンプレートと SharePoint ソリューションの作成に使用できる項目テンプレートのセットが含まれています。 たとえば、イベント レシーバー、リスト定義、ワークフロー、および Web パーツ用のテンプレートがあります。 ただし、SharePoint プロジェクト項目のフィールドまたはカスタム動作などの SharePoint コンポーネントを作成するための独自の型を定義することもできます。 SharePoint プロジェクト項目の種類の Visual Studio で、既にインストールされている拡張機能を作成することもでき、SharePoint プロジェクト用の拡張機能を作成することができます。  
  
 詳細については、次を参照してください。 [SharePoint プロジェクト システムを拡張する](../sharepoint/extending-the-sharepoint-project-system.md)です。  
  
### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張します。
 Visual Studio で、使用することができます、 **SharePoint 接続**内のノード、**サーバー エクスプ ローラー**を階層ツリー ビューで 1 つのコンポーネントの多くは以上のローカル SharePoint サイトを表示するウィンドウです。 拡張することも、 **SharePoint 接続**次のようにノード。  
  
-   独自のノードを追加します。 これは、既定で表示されていない SharePoint サイトのコンポーネントを表示する場合に便利です。  
  
-   既存のノードを拡張します。 たとえば、新しい子ノードを追加するには、既存のノードにまたはノードにショートカット メニュー項目を追加して、開発者は、メニュー項目をクリックしたときにタスクを実行します。  
  
 詳細については、次を参照してください。[サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張する](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)です。  
  
## <a name="development-computer-requirements"></a>開発コンピューターの要件
 SharePoint ツールの拡張機能を作成するには、開発用コンピューターが Visual Studio で SharePoint ソリューションを作成する場合に同じ要件を満たす必要があります。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
 インストールすることをお勧め、[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]です。 SDK には、プロジェクト テンプレートと Visual Studio の拡張に使用できるツールが含まれています。 具体的には、SDK には、Visual Studio Extension (VSIX) パッケージを簡単に作成に使用できるプロジェクト テンプレートが含まれています。 VSIX パッケージは、Visual Studio での Visual Studio 拡張機能を展開することをお勧めします。 すべての SharePoint ツール拡張機能は、VSIX パッケージを使用して展開する必要があります。 すべてのチュートリアルでは、このドキュメントのあるものと想定する、[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]インストールします。  
  
 Visual Studio SDK をインストールするを参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。 Visual Studio 拡張機能の詳細については、次を参照してください。 [Visual Studio 拡張機能の開発を開始して](../extensibility/starting-to-develop-visual-studio-extensions.md)です。  
  
## <a name="see-also"></a>関連項目
 [ツールの拡張機能を SharePoint のプログラミング モデルの概要](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [SharePoint プロジェクト システムの拡張](../sharepoint/extending-the-sharepoint-project-system.md)   
 [サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [プログラミングに関する概念との SharePoint ツール拡張機能](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [参照&#40;SharePoint ツールの拡張性&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Visual Studio での SharePoint ツールの拡張機能のデバッグ](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  
