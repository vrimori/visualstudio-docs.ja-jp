---
title: "方法: マスター ページまたはテーマをインポートする | Microsoft Docs"
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
  - "インポート (項目を) [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, インポート (項目を)"
ms.assetid: 8b446cca-2adb-457b-bbfd-891209290e80
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 方法: マスター ページまたはテーマをインポートする
  マスター ページとテーマを作成および使用して、SharePoint サイトのページに一貫した外観を与えることができます。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は これらの要素には、テンプレートでは、SharePoint Designer で作成し、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]にインポートできます。  詳細については Microsoft の [ビルド ブロック: ページおよびユーザー インターフェイス](http://go.microsoft.com/fwlink/?LinkID=182095) Web サイトでは、参照します。  
  
### マスター ページまたはテーマをインポートするには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で、SharePoint プロジェクトを作成または開きます。  
  
     SharePoint プロジェクトを作成する方法の詳細については、「[SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)」を参照してください。  
  
2.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[SharePoint\]** ノードを展開し、**\[2010\]** ノードを選択します。  
  
4.  SharePoint テンプレートの一覧で、**\[モジュール\]** テンプレートを選択し、モジュールの名前を指定します。  
  
     モジュールは、SharePoint で指定した場所に配置のファイル \(マスター ページまたはテーマ ファイル\) が含まれています。  
  
5.  モジュールでは、Sample.txt という名前の既定のファイルを削除します。  
  
6.  モジュール ノードをクリックします。  
  
7.  メニュー バーで、**\[既存のアイテムを追加\]\[プロジェクト\]** をクリックします、マスター ページ ファイルまたはテーマ ファイルを選択します。  
  
     マスター ページ ファイルに .master 拡張機能があり、テーマに .thmx ファイル拡張子が付きます。  
  
8.  マスター ページを追加する場合は、設定するモジュールのプロパティの **\[自動\]** に **\[配置競合の解決\]** を変更します。  
  
    > [!NOTE]  
    >  エラーは、マスター ページの名前が、既定のマスター ページまたはカスタム マスター ページとしてマークされた既存のマスター ページと同じである場合に発生します。  この問題の解決方法については、「[チュートリアル: イメージを備えたカスタム マスター ページおよびサイト ページのインポート](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)」を参照してください。  
  
9. モジュールには、Elements.xml ファイルを開きます。  
  
     追加したマスター ページまたはテーマが参照されるように Elements.xml ファイルを更新する必要があります。  
  
10. マスター ページを参照する場合は、既存のマークアップを次のコードに置き換えます。  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     テーマを参照する場合は、既存のモジュールのマークアップを次のマークアップに置き換えます。  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     プレースホルダーの値を、モジュール、マスター ページ、またはテーマの実際の名前に必ず置き換えてください。  
  
     `Type="GhostableInLibrary"` 属性はコンテンツ データベースに追加する項目を示し、モジュールの `Url` 属性は SharePoint コンテンツ データベース内のファイルの格納場所を指定します。  
  
11. マスター ページの配置スコープを、**\[ソリューション エクスプローラー\]** に変更するには、フィーチャー デザイナーのフィーチャー ファイルを開き、**\[スコープ\]** の一覧から新しい配置スコープを選択します。  
  
     **\[Web\]** の値はマスター ページがプロジェクト内に現在指定されているサイトにのみ適用されることを意味します。  **\[サイト\]** の値はマスター ページをすべてのサブサイトとルート Web が、現在のサイト コレクションに適用されることを意味します。  そのほかの値は適用されません。  
  
    > [!NOTE]  
    >  テーマはサイト コレクション レベルにのみ適用されるため、**\[サイト\]** 以外にテーマのスコープを設定しないことをお勧めします。  テーマがサブサイトで使用されると、エラーが発生する可能性があります。  
  
12. メニュー バーで、**\[ソリューションの配置\]\[ビルド\]** をクリックします。  
  
13. ファイルが正常に配置され、SharePoint サイトを開き、**\[サイトの操作\]** メニューをクリックし、**\[サイトの設定\]** コマンドを選択し、選択するかどうかを確認するには **\[マスター ページ\]** リンクまたは **\[テーマ\]** リンクを示します。  
  
     マスター ページまたはテーマ リストは、インポートしたマスター ページまたはテーマが表示され、格納されます。  
  
## 参照  
 [マスター ページ](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [既存の SharePoint サイトからのアイテムのインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint 用ページの作成](../sharepoint/creating-pages-for-sharepoint.md)   
 [モジュールを使用してソリューションにファイルを追加する](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  