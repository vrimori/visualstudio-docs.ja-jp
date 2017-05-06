---
title: "SharePoint へのビジネス データの統合"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio での SharePoint 開発], 集計 (データを)"
  - "BDC [Visual Studio での SharePoint 開発], ビジネス データ"
  - "BDC [Visual Studio での SharePoint 開発], 作成 (モデルを)"
  - "BDC [Visual Studio での SharePoint 開発], データ"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 集計 (データを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], ビジネス データ"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 作成 (モデルを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], データ"
ms.assetid: e092e3d6-2c5f-4060-ae86-d37db8967559
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# SharePoint へのビジネス データの統合
  SharePoint には、ビジネス データを統合することができます。  ビジネス データは、[!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)]、Siebel、SAP、Web サービスなどのバック エンドのサーバー アプリケーションから取得できます。  ユーザーは、SharePoint で外部リストまたはビジネス データ Web パーツを使用して、ビジネス データを表示、追加、更新、または削除できます。また、Microsoft Outlook などの Microsoft Office アプリケーションで、このデータにオフラインでアクセスできます。  詳細については、参照します[外部データを示すことができます。](http://go.microsoft.com/fwlink/?LinkId=169295)。  
  
 SharePoint にデータを統合するには、Business Data Connectivity \(BDC\) サービスのモデルを作成します。  BDC サービスは、ビジネス アプリケーションのデータに関する情報を格納する、SharePoint 内のアプリケーションです。  詳細については、参照します [Business Data Connectivity \(BDC\) サービス](http://go.microsoft.com/fwlink/?LinkID=169276)。  
  
## Visual Studio のモデル  
 Visual Studio のモデルを使用して、バックエンド データ ソースからデータを取得したり更新したりするカスタム コードを作成することができます。  複数のデータ ソースからのデータを集約することもできます。  たとえば、[!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] データベースと Web サービスから取得したデータを顧客一覧として表示できます。  
  
 既に SharePoint に配置されているモデルをインポートすることもできます。  モデルのインポート後は、カスタム コードを追加するか、Visual Studio でモデルをそのままパッケージ化し、複数の SharePoint サーバー ファームに配置することができます。  詳細については、「[ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)」を参照してください。  
  
## Visual Studio でのモデルのデザイン  
 モデルは、デザイナーのほか、いくつかのツール ウィンドウを使用してデザインできます。  モデルをデザインすると、同時に Visual Studio によってモデルの XML が生成されます。  詳細については、「[BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)」を参照してください。  
  
 モデルには、エンティティとメソッドが含まれています。  
  
### エンティティ  
 エンティティは、フィールドのコレクションを表します。  たとえば、データベース内のテーブルをエンティティで表現できます。  SharePoint で、エンティティは外部コンテンツ タイプとして表示されます。  外部コンテンツ タイプの詳細については、参照します [外部コンテンツ タイプとは何ですか。](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### メソッド  
 外部コンテンツ タイプの使用者は、エンティティのフィールドに対して特定のアクションを実行できます。それを可能にするのがメソッドです。  たとえば、`Customer` エンティティに `Address` フィールドと `BirthDate` フィールドがある場合、Updater メソッドを使用して、顧客の誕生日や住所を変更することができます。  
  
 Visual Studio では、モデル内のエンティティごとにサービス コード ファイルが生成されます。  モデルにメソッドを追加すると、対応するメソッドがサービス コード ファイル内に生成されます。  それぞれのメソッドには、必要なタスクを実行するコードを追加します。  たとえば、モデルに作成メソッドを追加すると、サービス コード ファイルに作成メソッドが生成されます。  このモデルをベースに作成されたリストの **\[新しいアイテム\]** ボタンをユーザーがクリックすると、このメソッドが BDC サービスによって呼び出されます。  したがって、作成メソッドには、データ ソースに新しいデータを登録するためのコードを追加することになります。  詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)|新しいモデルを作成したり、SharePoint からエクスポートしたモデルをインポートしたりする方法について説明します。|  
|[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)|Visual Studio のデザイン ツールを使用して、モデルの要素をデザインする方法について説明します。|  
|[いつ BCS を使用してソリューションをビルドすると、Visual Studio は SharePoint Designer を使用できます。](http://go.microsoft.com/fwlink/?LinkID=183448)|BDC 用のモデルを作成するときに Visual Studio と SharePoint Designer のどちらを使用するかを判断するのに役立ちます。|  
  
  