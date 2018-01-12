---
title: "SharePoint にビジネス データの統合 |Microsoft ドキュメント"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c054049c09f13c224ee4f0bb3021af1121f5cea8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="integrating-business-data-into-sharepoint"></a>SharePoint へのビジネス データの統合
  SharePoint にビジネス データを統合することができます。 ビジネス データがなどのバック エンド サーバー アプリケーションから取得できます[!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)]Siebel、および SAP、または Web サービスです。 ユーザーは、表示、追加、更新、または外部リストまたは SharePoint でのビジネス データ Web パーツを使用してビジネス データを削除できます。  ユーザーは、Microsoft Outlook などの Microsoft Office アプリケーションでこのデータをオフラインにもアクセスできます。 詳細については、次を参照してください。[場所できますする外部データの表示](http://go.microsoft.com/fwlink/?LinkId=169295)です。  
  
 を SharePoint にデータを統合するには、ビジネス データ接続 (BDC) サービスのモデルを作成します。 BDC サービスは、ビジネス アプリケーションでデータの情報を格納する SharePoint のアプリケーションです。 詳細については、次を参照してください。[ビジネス データ接続 (BDC) サービス](http://go.microsoft.com/fwlink/?LinkID=169276)です。  
  
## <a name="models-in-visual-studio"></a>Visual Studio のモデル  
 Visual Studio でモデルを使用すると、取得およびバックエンド データ ソースからデータを更新するカスタム コードを記述できます。 複数のデータ ソースからデータを集計することもできます。 たとえばからデータを含む顧客の一覧を表示することができます、[!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]データベースと Web サービスです。  
  
 SharePoint に既に配置されているモデルをインポートすることもできます。 モデルをインポートした後は、カスタム コードを追加またはだけ Visual Studio を使用してパッケージ化し、モデルが複数の SharePoint サーバー ファームに展開できます。 詳細については、次を参照してください。[ビジネス データ接続モデルを作成する](../sharepoint/creating-a-business-data-connectivity-model.md)です。  
  
## <a name="designing-a-model-in-visual-studio"></a>Visual Studio でモデルの設計  
 デザイナーといくつかのツール ウィンドウを使用してモデルを設計することができます。 モデルを設計する際、Visual Studio は、モデルの XML を生成します。 詳細については、次を参照してください。 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)です。  
  
 モデルには、エンティティとメソッドが含まれています。  
  
### <a name="entities"></a>エンティティ  
 エンティティは、フィールドのコレクションを表します。 たとえば、エンティティは、データベース内のテーブルを表すことができます。 エンティティは、SharePoint の外部コンテンツ タイプとして表示されます。 外部コンテンツ タイプの詳細については、次を参照してください[外部コンテンツ タイプをは何ですか?。](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>メソッド  
 メソッドは、エンティティのフィールドに操作を実行する外部コンテンツ タイプのコンシューマーを使用できます。 たとえば、Updater メソッドが、アドレスを変更するユーザーを有効にし、生年月日、顧客の可能性があります、`Address`と`BirthDate`のフィールド、`Customer`エンティティです。  
  
 Visual Studio では、モデル内の各エンティティ サービス コード ファイルが生成されます。 モデルにメソッドを追加するときに Visual Studio では、サービス コード ファイル内の対応するメソッドが生成されます。 適切なタスクを実行するには、各メソッドにコードを追加します。 たとえば、Creator メソッドをモデルに追加すると場合、Visual Studio は、サービス コード ファイルで Creator メソッドを生成します。 このメソッドは、BDC サービスによって、ユーザーがクリックしたときに、**新しい項目の**モデルに基づいている一覧のボタンをクリックします。 そのため、データ ソースに新しいデータを追加する Creator メソッドにコードを追加します。 詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)です。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)|新しいモデルを作成または sharepoint サイトからエクスポートしたモデルのインポートがする方法を示しています。|  
|[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)|Visual Studio デザイン ツールを使用して、モデルの要素をデザインする方法について説明します。|  
|[SharePoint デザイナーの使用とする場合。BCS を使用して visual Studio の作成時のソリューション](http://go.microsoft.com/fwlink/?LinkID=183448)|Visual Studio を使用または SharePoint デザイナーを使用して、bdc モデルを作成するかどうかを決定するのに役立ちます。|  
  
  