---
title: "方法: モジュールを使用して、ファイルを含める |Microsoft ドキュメント"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
ms.assetid: 16ac3c3b-8219-466c-8550-6109357f2f9a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3dca463352d5e698b74ecc6bda2a1579e3290513
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-include-files-by-using-a-module"></a>方法: モジュールを使用してファイルを含める
  *モジュール*(と混同しないでください[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]モジュール) を使用すると、SharePoint に ASPX マスター ページなどのファイル、テキスト ファイル、またはイメージを配置するコンテナーです。  
  
 ドキュメント ライブラリの外部ファイルを配置する、または通常のファイル (たとえば、default.aspx) として、ドキュメント ライブラリに選択できます。 ドキュメント ライブラリにファイルを追加するには指定`Type="GhostableInLibrary"`内の属性として、**ファイル**要素。 この設定では、SharePoint ライブラリに追加されたとき、ファイルを使用するリスト項目を作成するように指示します。 指定するか、ドキュメント ライブラリの外部ファイルを展開する`Type="Ghostable"`だけを省略するか、**型**属性。  
  
## <a name="adding-a-module-to-a-sharepoint-solution"></a>SharePoint ソリューションにモジュールを追加します。  
  
#### <a name="to-add-a-module"></a>モジュールを追加するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を開くか、SharePoint プロジェクトを作成します。  
  
     詳細については、次を参照してください。 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)です。  
  
2.  **ソリューション エクスプ ローラー**、プロジェクト ノードを選択し、次に、メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
     **[新しい項目の追加]** ダイアログ ボックスが開きます。  
  
3.  SharePoint テンプレートの一覧で選択、**モジュール**テンプレートを選択し、**追加**ボタンをクリックします。  
  
     この手順では、Module1 をという名前のプロジェクト ノードを作成します。  
  
4.  Module1、下、Sample.txt ファイルを削除します。  
  
     Sample.txt は、すべての新しいモジュールなどの目的に含まれは必要ありません。 (ファイルを削除してもから削除するエントリ、モジュールの Elements.xml ファイルに注意してください)。  
  
5.  Module1 下にあるそれらのフォルダーを作成する場合は、SharePoint 内の特定のフォルダー構造に配置する、ファイル、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Module1 ノードを選択し、メニュー バーで **プロジェクト**、**新規フォルダー**です。  
  
6.  ファイルを追加し、次に、メニュー バーで、次のように選択します。 フォルダーを選択して**プロジェクト**、**既存項目の追加**です。  
  
7.  クリックして、SharePoint に展開する 1 つまたは複数のファイルを選択して、**追加**ボタンをクリックします。  
  
     ファイルをプロジェクトに追加するときに、モジュールの Elements.xml ファイルにエントリが自動的に追加します。 指定されているプロジェクトのルート ディレクトリに対して相対的な SharePoint サーバーにファイルをコピー、プロジェクトを配置するときに、**ファイル**要素の**Url**属性など`Url="Module1/New Folder/SomeFile.doc`です。 別のフォルダーに移動するか、ファイルの配置場所を変更する場合は、**ソリューション エクスプ ローラー**を変更またはその**Url**設定します。  
  
8.  ドキュメント ライブラリに表示する、ファイルを追加、`Type="GhostableInLibrary"`属性 Elements.xml 内のエントリをします。 たとえば、オブジェクトに適用された  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. プロジェクトを展開します。  
  
     ファイルは、SharePoint での指定された場所にコピーします。  
  
## <a name="see-also"></a>参照  
 [パッケージ化と SharePoint ソリューションの配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
  