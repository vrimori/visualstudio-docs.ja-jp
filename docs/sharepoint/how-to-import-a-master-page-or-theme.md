---
title: '方法: マスター ページまたはテーマのインポート |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: af0f7ad40c1e06f1c602f17ba6a80cf47b96ed0e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863371"
---
# <a name="how-to-import-a-master-page-or-theme"></a>方法: マスター ページまたはテーマをインポートします。
  付与できますページ、SharePoint サイトで一貫した外観を作成してマスター ページとテーマを使用します。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] これらの要素のテンプレートが指定されない SharePoint Designer で作成できにインポートできますが、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 詳細については、次を参照してください。[ビルディング ブロック。ページとユーザー インターフェイス](http://go.microsoft.com/fwlink/?LinkID=182095)Microsoft web サイト。  
  
### <a name="to-import-a-master-page-or-theme"></a>マスター ページまたはテーマをインポートするには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を作成または SharePoint プロジェクトを開きます。  
  
     SharePoint プロジェクトを作成する方法については、次を参照してください。 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)します。  
  
2.  メニュー バーで **[プロジェクト]** > **[新しい項目の追加]** の順に選択します。  
  
3.  **新しい項目の追加** ダイアログ ボックスで、展開、 **SharePoint**ノードを選択し、 **2010**ノード。  
  
4.  SharePoint テンプレートの一覧で選択、**モジュール**テンプレート、モジュールの名前を指定します。  
  
     モジュールには、SharePoint で指定した場所に配置するためのファイル (たとえば、マスター ページまたはテーマ ファイル) が含まれています。  
  
5.  モジュールで、削除の既定のファイルの名前は*Sample.txt*します。  
  
6.  モジュール ノードを選択します。  
  
7.  メニュー バーで、**プロジェクト** > **既存項目の追加**、マスター ページまたはテーマ ファイルを選択します。  
  
     マスター ページのファイル拡張子を持ち、.master、およびテーマ ファイル .thmx という拡張子があります。  
  
8.  マスター ページを追加した場合は、変更、**配置競合の解決**設定**自動**モジュールのプロパティで。  
  
    > [!NOTE]  
    >  エラーは、マスター ページの名前は既定のマスター ページまたはカスタム マスター ページのいずれかとしてマークされている既存のマスター ページの名前と同じ場合に発生することができます。 この問題を解決する方法については、次を参照してください。[チュートリアル。カスタム マスター ページとサイトのページにイメージをインポート](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)します。  
  
9. モジュールで、開く*Elements.xml*します。  
  
     更新する必要があります、 *Elements.xml*マスター ページまたはテーマを追加するを参照するファイル。  
  
10. マスター ページのモジュールの既存のマークアップを次のマークアップに置き換えます。  
  
    ```xml  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     テーマのモジュールの既存のマークアップを次のマークアップに置き換えます。  
  
    ```xml  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     必ず、プレース ホルダーの値をモジュールとマスター ページまたはテーマの実際の名前に置き換えます。  
  
     属性`Type="GhostableInLibrary"`、コンテンツ データベースに項目を追加することを示します、`Url`モジュールの属性は、ファイルを SharePoint コンテンツ データベースに保存する場所を指定します。  
  
11. マスター ページのデプロイの範囲を変更する**ソリューション エクスプ ローラー**、デザイナーの機能で機能ファイルを開きからの新しい配置スコープを選択し、**スコープ**一覧。  
  
     値**Web**マスター ページは、プロジェクトで現在指定されている web サイトにのみ適用されることを意味します。 値**サイト**マスター ページは、すべてのサブサイトとルート web を含む現在のサイト コレクションに適用されることを意味します。 その他の値は適用されません。  
  
    > [!NOTE]  
    >  設定することはありません、テーマのスコープに何も以外のテーマは、サイト コレクション レベルにのみ適用される、ので推奨**サイト**します。 エラーは、サブ サイトにテーマを使用する場合に発生します。  
  
12. メニュー バーで、**ビルド** > **ソリューションの配置**します。  
  
13. ファイルが正しく展開されているかどうかを確認するには、SharePoint サイトを開き、**サイトの操作**メニューで、選択、**サイト設定**コマンドを使用し、いずれかを選択し、**マスター ページ**リンクまたは**テーマ**リンク。  
  
     マスター ページまたはテーマのいずれかのリストが表示され、マスター ページまたはインポートしたテーマのいずれかが含まれています。  
  
## <a name="see-also"></a>関連項目
 [マスター ページ](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [既存の SharePoint サイトからのアイテムのインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint 用ページを作成します。](../sharepoint/creating-pages-for-sharepoint.md)   
 [モジュールを使用して、ソリューションにファイルを含める](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
