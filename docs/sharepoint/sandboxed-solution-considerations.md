---
title: サンド ボックス ソリューションの考慮事項 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2f9a5d0c439d619864cc6e9559608e3c3891fc7e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890037"
---
# <a name="sandboxed-solution-considerations"></a>サンド ボックス ソリューションの考慮事項
  *サンド ボックス ソリューション*は Microsoft SharePoint 2010 サイト コレクションのユーザーが独自のカスタム コード ソリューションをアップロードできるようにする機能です。 一般的なサンド ボックス ソリューションは、ユーザーが自分の Web パーツをアップロードします。  
  
 セキュリティで保護された SharePoint アプリケーションは、Web ファームの一部にアクセスできるセキュリティで保護された、監視対象のプロセスで実行されます。 Microsoft SharePoint 2010 では、サンド ボックス ソリューションを有効にするのに機能、ソリューション ギャラリー、ソリューションの監視、および検証フレームワークの組み合わせを使用します。  
  
## <a name="specify-project-trust-level"></a>プロジェクトの信頼レベルを指定します
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] サポートする project のブール型プロパティを通じてサンド ボックス ソリューションと呼ばれる*サンド ボックス ソリューション*します。 このプロパティは、プロジェクトで、いつでも設定できますかでプロジェクトを作成するときに指定が、 **SharePoint カスタマイズ ウィザード**します。  
  
> [!NOTE]  
>  変更、*サンド ボックス ソリューション*作成後、プロジェクトのプロパティの検証エラーが発生する可能性があります。  
  
 場合、ソリューションはファーム スコープのソリューションと見なされます、*サンド ボックス ソリューション*プロパティに設定されて**false**ことも、**ファーム ソリューションとして配置**オプション。 ただし、ソリューションは扱いがファーム ソリューションの場合、*サンド ボックス ソリューション*プロパティに設定されて**true**ことも、**サンド ボックス ソリューションとして配置**ウィザードのオプション。  
  
## <a name="sharepoint-site-hierarchy"></a>SharePoint サイトの階層
 どのサンド ボックス ソリューションを理解する SharePoint サイトは、スコープ内で階層を把握する作業に役立ちます。 最上位の要素は、Web ファームと呼ばれ、他の要素が従属します。  
  
 Web ファーム  
  
 Web アプリケーション A  
  
 サイト コレクションの A1  
  
 サイト A1a  
  
 Web アプリケーション B  
  
 サイト コレクションの B1  
  
 サイト B1a  
  
 サイト B1b  
  
 サイト コレクション B2  
  
 サイト B2a  
  
 ご覧のように、Web ファームにさらに、サブサイトとに、1 つまたは複数のサイト コレクションを含めることができますが、1 つまたは複数の Web アプリケーションを含めることができます。 サイト コレクションのみを 1 つのサイト コレクションにしての他の変更します。 ただし、Web ファーム レベルで行われた変更は、ファーム上のすべてのサイト コレクションに影響します。  
  
 Windows SharePoint Services (WSS) 3.0 では、ファーム レベルにのみ、ソリューションをデプロイできますが、 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] (ファーム ソリューション) ファーム レベルまたはサイト コレクション レベル (サンド ボックス ソリューション) のいずれかにデプロイすることができます。  
  
## <a name="why-sandboxed-solutions"></a>なぜサンド ボックス ソリューションでしょうか。
 WSS 3.0 では、ソリューションをファーム レベルにのみ展開可能性があります。 これは、ため、有害なまたは安定性を損なう可能性があるソリューションが配置されると Web ファーム全体とその他のサイト コレクションおよびその下で実行されるアプリケーションのすべての影響を受けます。 ただし、サンド ボックス ソリューションを使用して、ファームでは、特定のサイト コレクションのサブ区分をソリューションをデプロイできます。 追加の保護を提供するソリューションのアセンブリが、メイン読み込まれない[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]プロセス (*w3wp.exe*)。 代わりに、別のプロセスに読み込まれる (*SPUCWorkerProcess.exe*)。 このプロセスは、監視し、クォータと CPU サイクルを消費する厳密なループ処理を実行しているなどの有害なアクティビティを実行するサンド ボックス ソリューションから、ファームを保護するために調整を実装します。  
  
## <a name="site-collection-solution-gallery"></a>サイト コレクションのソリューション ギャラリー
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 には、「サイト コレクション ソリューション ギャラリー」と呼ばれる機能 この機能をアクセスするには、SharePoint 2010 サーバーの全体管理ページから開くか、**サイトの操作**] メニューの [選択**サイトの設定**、選択し、 **ソリューション** ] にある [**ギャラリー** SharePoint サイトにします。 ソリューション ギャラリーは、そのサイト コレクションでソリューションを管理するサイト コレクション管理者を有効にするソリューションのリポジトリです。  
  
 ソリューション ギャラリーは、SharePoint サイトの Web ルートに格納されているドキュメント ライブラリです。 ソリューション ギャラリーを使用して、サイト テンプレートを置き換えられ、ソリューション パッケージをサポートしています。 ときに、SharePoint ソリューション パッケージ (*.wsp*) ファイルをアップロード、サンド ボックス ソリューションとして処理されます。  
  
## <a name="sandboxed-solution-limitations"></a>サンド ボックス ソリューションの制限事項
 サンド ボックス ソリューションの配置に使用可能な SharePoint 機能の配列があること、セキュリティの脆弱性を減らすために制限されます。 これらの制限の一部を以下に示します。  
  
- サンド ボックス ソリューションのデプロイ可能なソリューションの要素が使用できるようにする制限されたサブセットがあります。 サイト定義、ワークフローなどの脆弱性のある可能性がある SharePoint プロジェクト テンプレートは使用できません。  
  
- SharePoint のプロセスでサンド ボックス ソリューションのコードを実行する (*SPUCWorkerProcess.exe*)、main から独立した[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]アプリケーション プール (*w3wp.exe*) プロセス。  
  
- マップされたフォルダーは、プロジェクトに追加することはできません。  
  
- 型、[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]アセンブリ Microsoft.Office.Server はサンド ボックス ソリューションでは使用できません。 また、のみの型、[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]アセンブリ Microsoft.SharePoint をサンド ボックス ソリューションで使用できます。  
  
  指定する SharePoint ソリューション、サンド ボックス ソリューション SharePoint サーバー上に影響があるないとすることが重要SharePoint を SharePoint プロジェクトを展開する方法を示すのみ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]とどのようなアセンブリをバインドします。 影響しません、生成された *.wsp*ファイル、および *.wsp*ファイルに直接関連するデータがない、*サンド ボックス ソリューション*プロパティ。  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>サンド ボックス ソリューションの機能と要素
 サンド ボックス ソリューションは、次の機能や要素をサポートします。  
  
- コンテンツの種類/フィールド  
  
- カスタム アクション  
  
- 宣言型ワークフロー  
  
- イベント レシーバー  
  
- 機能の吹き出し  
  
- リストの定義  
  
- リスト インスタンス  
  
- モジュール/ファイル  
  
- ナビゲーション  
  
- *Onet.xml*  
  
- SPItemEventReceiver  
  
- SPListEventReceiver  
  
- SPWebEventReceiver  
  
- 派生したすべての Web パーツのサポート `System.Web.UI.WebControls.WebParts.WebPart`  
  
- Web パーツ  
  
- Web テンプレート機能の要素 (の代わりに*Webtemp.xml*)  
  
- 視覚的 Web パーツ  
  
  サンド ボックス ソリューションは、次の機能と要素はサポートされません。  
  
- アプリケーション ページ  
  
- カスタム アクション グループ  
  
- ファーム スコープの機能  
  
- `HideCustomAction` 要素  
  
- Web アプリケーション スコープの機能  
  
- コードでのワークフロー  
  
## <a name="see-also"></a>関連項目
 [サンド ボックスの相違点とファーム ソリューション](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  