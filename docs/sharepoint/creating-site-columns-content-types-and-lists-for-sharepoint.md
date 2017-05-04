---
title: "SharePoint のサイト列、コンテンツ タイプ、およびリストの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.ListDesigner.ContentTypeSetting"
  - "VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage"
  - "VS.SharePointTools.ListDesigner.CreatingLists"
  - "VS.SharePointTools.ListDesigner.ListPage"
  - "VS.SharePointTools.ListDesigner.ViewPage"
  - "VS.SharePointTools.ListDesigner.CommonPropertiesPage"
  - "VS.SharePointTools.ContentTypeDesigner.ColumnsPage"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 9ceed263-3aec-41dc-8708-63cb37a08fa8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# SharePoint のサイト列、コンテンツ タイプ、およびリストの作成
  Visual Studio は、サイト内の列できる *コンテンツ タイプ*提供、および *リスト* が SharePoint さまざまな基本的な項目にプロジェクト項目テンプレートを、\(または *フィールド*\) を組み込む。  コンテンツ タイプやリストの新しいデザイナーはやすくなります。これらの項目を作成します。  
  
## サイト列  
 サイト内の列は SharePoint プロジェクトに追加できるほとんどの基本要素の 1 つです。  サイト内の列が連絡先一覧の連絡先電話番号、コメント、または市の名前などのデータ型を表します。  
  
 新しいサイト内の列プロジェクト項目テンプレートは、やすくなります。サイト内の列を Visual Studio の旧バージョンでも作成します。  新しいサイト内の列を作成したら、表示名などのデータ型を使用すると、サイト内の列の SharePoint に表示するグループは、情報を含めるようにサイト内の列の Elements.xml ファイル内の XML を変更します。  サイト内の列の詳細については、参照 [列について](http://go.microsoft.com/fwlink/?LinkId=224996)します。  
  
## コンテンツ タイプやリスト  
 コンテンツ タイプやリストは、SharePoint で最もよく使用される要素間にあります。  
  
 コンテンツ タイプは、SharePoint リストまたはドキュメント ライブラリの項目のカテゴリのメタデータ、およびワークフロー動作を定義します。  たとえば、連絡先リストやタスク一覧情報のコンテンツ タイプを作成できます。  連絡先のコンテンツ タイプには名前、電子メール アドレス、電話番号、などの列が含まれる場合があります。  サイト レベルで定義するコンテンツ タイプはサイトの一覧またはドキュメント ライブラリに依存しません。  SharePoint サイトの異なるリストまたはドキュメント ライブラリと同じコンテンツ タイプを使用できます。  同じリストまたはドキュメント ライブラリのコンテンツ タイプを使用できます。  
  
 リストには、他のユーザーと共有できる SharePoint の情報のコレクションです。  リストのデータを含む列の行から構成されます。  リストの例は次のとおりです。: タスク一覧には、連絡先リスト、通知を選択します。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の新しいコンテンツ タイプやリストのデザイナーが簡単で、Visual Studio の旧バージョンで直感的なサイト コンテンツ タイプやリストも作成できるようになります。  UI によって、一般的な方法でコンテンツ タイプやリストを生成するようにするとリストのグループ データを並べ替え、グループの見出しを使用できるようになります。  コンテンツ タイプの詳細については、参照します [コンテンツ タイプ](http://go.microsoft.com/fwlink/?LinkId=224997)。  リストの詳細については、[リスト形式](http://go.microsoft.com/fwlink/?LinkId=224998) 参照します [リスト ビュー](http://go.microsoft.com/fwlink/?LinkId=224999)。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[チュートリアル: SharePoint のサイト列、コンテンツ タイプ、およびリストの作成](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|カスタム コンテンツ タイプで使用するサイト内の列を作成する方法を示します。  コンテンツ タイプはカスタム リストで使用されます。|  
  
## 参照  
 [SharePoint 2010 の開発を開始します。](http://go.microsoft.com/fwlink/?LinkId=225000)  
  
  