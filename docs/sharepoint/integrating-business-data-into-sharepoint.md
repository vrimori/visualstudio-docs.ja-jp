---
title: SharePoint にビジネス データの統合 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 194f2e0c88a0cbce9ef34f77246cf7969066833e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934441"
---
# <a name="integrate-business-data-into-sharepoint"></a>SharePoint ビジネス データを統合します。
  ビジネス データは、SharePoint に統合できます。 ビジネス データがなどのバック エンド サーバーのアプリケーションから取得できます[!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)]Siebel、および SAP、または Web サービス。 ユーザーは、表示、追加、更新、または外部リストまたは SharePoint のビジネス データ Web パーツを使用してビジネス データを削除できます。  ユーザーは、Microsoft Outlook などの Microsoft Office アプリケーションでこのデータをオフラインにもアクセスできます。 詳細については、次を参照してください。[場所できますする外部データの表示](http://go.microsoft.com/fwlink/?LinkId=169295)します。  
  
 SharePoint にデータを統合するには、ビジネス データ接続 (BDC) サービスのモデルを作成します。 BDC サービスは、ビジネス アプリケーションでデータに関する情報を格納する SharePoint のアプリケーションです。 詳細については、次を参照してください。[ビジネス データ接続 (BDC) サービス](http://go.microsoft.com/fwlink/?LinkID=169276)します。  
  
## <a name="models-in-visual-studio"></a>Visual Studio でモデル  
 Visual Studio でモデルを使用すると、取得およびバックエンド データ ソースからデータを更新するカスタム コードを記述できます。 複数のデータ ソースからデータを集計することもできます。 データを含む顧客の一覧を表示するなど、[!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]データベースと Web サービス。  
  
 SharePoint に既に配置されているモデルをインポートすることもできます。 モデルにインポートした後は、カスタム コードを追加またはだけパッケージ化し、複数の SharePoint サーバー ファームに、モデルをデプロイする Visual Studio を使用できます。 詳細については、次を参照してください。 [business data connectivity モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)です。  
  
## <a name="design-a-model-in-visual-studio"></a>Visual Studio でモデルを設計します。
 デザイナーといくつかのツール ウィンドウを使用してモデルを設計することができます。 モデルを設計する際、Visual Studio には、モデルの XML が生成されます。 詳細については、次を参照してください。 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)します。  
  
 モデルには、エンティティとメソッドが含まれています。  
  
### <a name="entities"></a>エンティティ  
 エンティティには、フィールドのコレクションについて説明します。 たとえば、エンティティは、データベース内のテーブルを表すことができます。 エンティティは、SharePoint の外部コンテンツ タイプとして表示されます。 外部コンテンツ タイプの詳細については、次を参照してください[外部コンテンツの種類は何ですか?。](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>メソッド  
 メソッドには、エンティティのフィールドの操作を実行する場合は、外部コンテンツ タイプのコンシューマーができます。 たとえば、Updater メソッドが、アドレスを変更するユーザーを有効にし、生年月日、顧客の可能性があります、`Address`と`BirthDate`のフィールドには、`Customer`エンティティ。  
  
 Visual Studio では、モデル内の各エンティティ サービス コード ファイルを生成します。 モデルにメソッドを追加するときに Visual Studio は、サービス コード ファイルに対応するメソッドを生成します。 適切なタスクを実行するには、各メソッドにコードを追加します。 たとえば、Creator メソッドをモデルに追加する場合 Visual Studio は、サービス コード ファイルで Creator メソッドを生成します。 ユーザーがクリックしたときに、BDC サービスでこのメソッドが呼び出されます、**新しい項目の**モデルに基づいている一覧でボタンをクリックします。 そのため、データ ソースに新しいデータを追加する作成者メソッドにコードを追加します。 詳細については、次を参照してください。[ビジネス データ接続モデルを設計する](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
## <a name="related-topics"></a>関連トピック
  
|タイトル|説明|  
|-----------|-----------------|  
|[ビジネス データ接続モデルを作成します。](../sharepoint/creating-a-business-data-connectivity-model.md)|方法、新しいモデルを作成または sharepoint サイトからエクスポートしたモデルのインポートを示しています。|  
|[ビジネス データ接続モデルを設計します。](../sharepoint/designing-a-business-data-connectivity-model.md)|Visual Studio デザイン ツールを使用してモデルの要素をデザインする方法について説明します。|  
|[Vs の SharePoint Designer を使用する場合。BCS を使用して visual Studio 開発ソリューション](http://go.microsoft.com/fwlink/?LinkID=183448)|Visual Studio を使用して、または SharePoint デザイナーを使用して、bdc モデルを作成するかどうかを判断します。|  
