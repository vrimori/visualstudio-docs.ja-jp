---
title: "方法: マスター ページまたはテーマをインポート |Microsoft ドキュメント"
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
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 07c3e9fb88ea562a85e1c7555d2c57cb04d769ff
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-import-a-master-page-or-theme"></a>方法: マスター ページまたはテーマをインポートする
  付与できるページ、SharePoint サイトで一貫した外観を作成し、マスター ページとテーマを使用します。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]これらの要素のテンプレートが用意されていませんが、SharePoint Designer で作成しにインポートできます[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 詳細については、次を参照してください。[ビルディング ブロック: ページやユーザー インターフェイス](http://go.microsoft.com/fwlink/?LinkID=182095)、Microsoft web サイトです。  
  
### <a name="to-import-a-master-page-or-theme"></a>マスター ページまたはテーマをインポートするには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を作成または SharePoint プロジェクトを開きます。  
  
     SharePoint プロジェクトを作成する方法については、次を参照してください。 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)です。  
  
2.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
3.  **新しい項目の追加** ダイアログ ボックスで、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
4.  SharePoint テンプレートの一覧で選択、**モジュール**テンプレート、モジュールの名前を指定します。  
  
     モジュールには、SharePoint で指定した場所に配置するためのファイル (たとえば、マスター ページまたはテーマ ファイル) が含まれています。  
  
5.  モジュールでは、Sample.txt の名前は既定のファイルを削除します。  
  
6.  モジュールのノードを選択します。  
  
7.  メニュー バーで、次のように選択します。**プロジェクト**、**既存項目の追加**、し、マスター ページまたはテーマ ファイルを選択します。  
  
     マスター ページ ファイル .master 拡張子は、テーマ ファイル .thmx 拡張子が付いています。  
  
8.  マスター ページを追加した場合は、変更、**配置競合の解決**設定**自動**モジュールのプロパティでします。  
  
    > [!NOTE]  
    >  エラーは、マスター ページの名前はマスター ページの既定またはカスタム マスター ページとしてマークされている既存のマスター ページの名前と同じ場合に発生することができます。 この問題を解決する方法については、次を参照してください。[チュートリアル: カスタム マスター ページと、イメージがあるサイト ページ インポート](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)です。  
  
9. モジュールでは、Elements.xml を開きます。  
  
     マスター ページまたは追加したテーマを参照する Elements.xml ファイルを更新する必要があります。  
  
10. マスター ページの既存のモジュールのマークアップを次のマークアップに置き換えます。  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     テーマの既存のモジュールのマークアップを次のマークアップに置き換えます。  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     必ず、プレース ホルダーの値をモジュールと、マスター ページまたはテーマの実際の名前に置き換えます。  
  
     属性`Type="GhostableInLibrary"`アイテムが、コンテンツ データベースに追加されたことを示す、`Url`モジュールの属性は、ファイルが SharePoint コンテンツ データベースに保存する場所を指定します。  
  
11. マスター ページの展開のスコープを変更する**ソリューション エクスプ ローラー**、フィーチャー デザイナーで機能ファイルを開くしから新しい配置スコープを選択し、**スコープ**リスト。  
  
     値**Web**マスター ページは、プロジェクトで現在指定されている web サイトにのみ適用されることを意味します。 値**サイト**マスター ページが、現在のサイト コレクション、すべてのサブサイト、ルート web などに適用されることを意味します。 その他の値は適用されません。  
  
    > [!NOTE]  
    >  あるしないスコープを設定するテーマの何もする以外のテーマは、サイト コレクション レベルにのみ適用される、ためお勧め**サイト**です。 エラーは、サブ サイトのテーマを使用する場合に発生します。  
  
12. メニュー バーで、次のように選択します。**ビルド**、**ソリューションの配置**です。  
  
13. ファイルが正しく展開されているかどうかを確認するには、SharePoint サイトを開きを選択、**サイトの操作**メニューで、選択、**サイト設定**コマンドを使用し、いずれかを選択、**マスター ページ**リンクまたは**テーマ**リンクします。  
  
     マスター ページまたはテーマのいずれかの一覧が表示され、マスター ページまたはインポートしたテーマのいずれかが含まれています。  
  
## <a name="see-also"></a>参照  
 [マスター ページ](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [既存の SharePoint サイトからアイテムをインポートします。](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint 用ページの作成](../sharepoint/creating-pages-for-sharepoint.md)   
 [モジュールを使用してソリューションにファイルを含める](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  