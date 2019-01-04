---
title: '方法: SharePoint の配置構成の編集 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 73b59e709ba75d5624f28cf80c9a5fdfdf8ee835
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843594"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>方法: SharePoint の配置構成を編集します。
  配置構成を作成または既存の展開構成を変更できます。 たとえば、1 つの手順を実行したり、展開プロセスの手順の順序を変更します。 作成または組み込みおよびプログラムで追加の構成を変更できないために、展開の構成を変更することがあります。  
  
## <a name="create-a-sharepoint-deployment-configuration"></a>SharePoint の配置構成を作成します。  
  
#### <a name="to-create-a-sharepoint-deployment-configuration"></a>SharePoint の配置構成を作成するには  
  
1.  **ソリューション エクスプ ローラー**を SharePoint プロジェクトを選択し、メニュー バーで、次のように選択します。**プロジェクト**、 _ProjectName_**プロパティ**します。  
  
2.  **SharePoint**  タブで、選択、**新規**ボタンをクリックします。  
  
     **新しい配置構成の追加** ダイアログ ボックスが表示されます。  
  
3.  **名前**テキスト ボックスに、展開の構成の名前を入力します。  
  
4.  **使用可能な展開手順**ウィンドウで、展開の構成に追加するには、選択する手順を選択、(**>**) ボタンをクリックし、選択し、 **[ok]** ボタンをクリックします。  
  
    > [!NOTE]  
    >  配置前コマンドまたは配置後コマンドを構成した場合、次の手順は、カスタマイズされた展開構成に追加する場合にのみを実行します。  
  
## <a name="change-the-active-deployment-configuration"></a>アクティブな配置構成を変更します。  
  
#### <a name="to-change-the-active-deployment-configuration"></a>アクティブな配置構成を変更するには  
  
1.  **ソリューション エクスプ ローラー**を SharePoint プロジェクトを選択し、メニュー バーで、次のように選択します**プロジェクト** > **\<*ProjectName*。> プロパティ**します。  
  
2.  選択、 **SharePoint**タブ。  
  
3.  **アクティブな配置構成**リスト ボックスで、使用する配置構成の名前を選択します。  
  
## <a name="see-also"></a>関連項目
 [パッケージ化し、SharePoint ソリューションのデプロイ](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
