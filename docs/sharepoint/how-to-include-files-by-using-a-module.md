---
title: '方法: モジュールを使用して、ファイルを含める |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5c5152221e5e58504ba84e0ad0f31511b4d93aa0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119382"
---
# <a name="how-to-include-files-by-using-a-module"></a>方法: モジュールを使用して、ファイルを含める
  *モジュール*(と混同しないように[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]モジュール) は、SharePoint にマスターの ASPX ページなどのファイル、テキスト ファイル、またはイメージをデプロイするためのコンテナーです。  
  
 ドキュメント ライブラリ外、または通常のファイル (たとえば、default.aspx) としてドキュメント ライブラリにファイルを展開する選択できます。 ドキュメント ライブラリにファイルを追加するには指定`Type="GhostableInLibrary"`属性として、**ファイル**要素。 この設定では、SharePoint ライブラリに追加されたとき、ファイルを使用するリスト項目を作成するように指示します。 指定するか、ドキュメント ライブラリの外部ファイルを展開する`Type="Ghostable"`を省略するか、**型**属性。  
  
## <a name="add-a-module-to-a-sharepoint-solution"></a>SharePoint ソリューションにモジュールを追加します。  
  
#### <a name="to-add-a-module"></a>モジュールを追加するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を開くか、SharePoint プロジェクトを作成します。  
  
     詳細については、次を参照してください。 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)します。  
  
2.  **ソリューション エクスプ ローラー**をプロジェクト ノードを選択し、メニュー バーで、次のように選択します。**プロジェクト** > **新しい項目の追加**します。  
  
     **[新しい項目の追加]** ダイアログ ボックスが開きます。  
  
3.  SharePoint テンプレートの一覧で選択、**モジュール**テンプレートを選択し、**追加**ボタンをクリックします。  
  
     この手順では、Module1 という名前のプロジェクトでノードを作成します。  
  
4.  Module1、削除、 *Sample.txt*ファイル。  
  
     Sample.txt は、すべての新しいモジュールなどの目的に含まれているしは必要ありません。 (注こと、ファイルを削除しても、エントリから削除しますモジュールの*Elements.xml*ファイルです)。  
  
5.  Module1 でそれらのフォルダーを作成、ファイルを SharePoint で特定のフォルダー構造を展開する場合は、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Module1] ノードを選択し、メニュー バーで [**プロジェクト**、**新規フォルダー**します。  
  
6.  ファイルを追加し、次に、メニュー バーで、次のように選択します。 フォルダーを選択**プロジェクト**、**既存項目の追加**します。  
  
7.  クリックして、SharePoint に配置する 1 つまたは複数のファイルの選択、**追加**ボタンをクリックします。  
  
     ファイルをプロジェクトに追加すると、モジュールの Elements.xml ファイルにエントリが自動的に追加します。 指定されているプロジェクトのルート ディレクトリに対する相対の SharePoint サーバーにファイルをコピー、プロジェクトを配置するときに、**ファイル**要素の**Url**属性など、`Url="Module1/New Folder/SomeFile.doc`します。 別のフォルダーに移動するかファイルの配置場所を変更する場合は、**ソリューション エクスプ ローラー**変更またはその**Url**設定します。  
  
8.  ドキュメント ライブラリに表示するすべてのファイルの追加、`Type="GhostableInLibrary"`属性内のエントリを*Elements.xml*します。 たとえば、オブジェクトに適用された  
  
    ```xml  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. プロジェクトをデプロイします。  
  
     ファイルは、SharePoint 内の指定の場所にコピーします。  
  
## <a name="see-also"></a>関連項目
 [パッケージ化し、SharePoint ソリューションのデプロイ](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
