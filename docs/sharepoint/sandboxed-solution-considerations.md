---
title: "サンド ボックス ソリューションの考慮事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: 6c2d2dc6-4acb-4b68-ba94-a61087e8dff0
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4598b100572bb47fd537e8edad927d78b4f1550
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sandboxed-solution-considerations"></a>Sandboxed Solution Considerations
  *サンド ボックス ソリューション*を独自のカスタム コード ソリューションをアップロードするサイト コレクションのユーザーを有効にする Microsoft SharePoint 2010 で機能します。 一般的なサンド ボックス ソリューションは、ユーザー独自の Web パーツのアップロードです。  
  
 セキュリティで保護された SharePoint アプリケーションは、Web ファームの一部にアクセスできるセキュリティで保護された、監視対象のプロセスで実行されます。 Microsoft SharePoint 2010 では、機能、ソリューション ギャラリー、ソリューションの監視、および検証フレームワークの組み合わせを使用して、サンド ボックス ソリューションを有効にします。  
  
## <a name="specifying-project-trust-level"></a>プロジェクトの信頼レベルを指定します。  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]サポートする project のブール型プロパティでサンド ボックス ソリューションと呼ばれる*サンド ボックス ソリューション*です。 このプロパティは、プロジェクトでいつでも設定できますかで、プロジェクトを作成する場合と指定することができます、 **SharePoint カスタマイズ ウィザード**です。  
  
> [!NOTE]  
>  変更、*サンド ボックス ソリューション*が作成された後、プロジェクトのプロパティの検証エラーが発生する可能性があります。  
  
 場合、ソリューションは、ファーム スコープ ソリューションと見なされます、*サンド ボックス ソリューション*プロパティに設定されている**false**選択することも、**ファーム ソリューションとして配置**オプション。 ただし、ソリューションの扱いはファーム ソリューションの場合、*サンド ボックス ソリューション*プロパティに設定されている**true**選択することも、**サンド ボックス ソリューションとして配置**ウィザードのオプションです。  
  
## <a name="sharepoint-site-hierarchy"></a>SharePoint サイトの階層  
 どのサンド ボックス ソリューションを理解している SharePoint サイトが階層構造にスコープを理解するのに役立ちます作業、します。 最上位の要素は、Web ファームとして知られ、その他の要素が従属します。  
  
 Web ファーム  
  
 Web アプリケーション A  
  
 サイト コレクション A1  
  
 サイト A1a  
  
 Web アプリケーション B  
  
 サイト コレクション B1  
  
 サイト B1a  
  
 サイト B1b  
  
 サイト コレクション B2  
  
 サイト B2a  
  
 ご覧のように、Web ファームは、さらに、サブサイトとに、1 つまたは複数のサイト コレクションを含めることができますが、1 つまたは複数の Web アプリケーションを含めることができます。 1 つのサイト コレクションにサイト コレクションを示すだけに行われたと他の変更します。 ただし、Web ファーム レベルで行われた変更は、ファーム上のすべてのサイト コレクションに影響します。  
  
 Windows SharePoint Services (WSS) 3.0 では、ファーム レベルにだけソリューションを配置することができますが、[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]ファーム レベル (ファーム ソリューション) またはサイト コレクション レベル (サンド ボックス ソリューション) のいずれかに展開することができます。  
  
## <a name="why-sandboxed-solutions"></a>なぜサンド ボックス ソリューションか。  
 WSS 3.0 では、ソリューションをファーム レベルにのみ展開できます。 これは、こと有害なまたは安定性を損なう可能性があるソリューションが配置されると、Web ファーム全体とすべての他のサイト コレクションとその下で実行されるアプリケーションに影響を意味していました。 ただし、サンド ボックス ソリューションを使用するは、ファームで特定のサイト コレクションのサブ区分に、ソリューションを配置することができます。 追加の保護を提供するにはソリューションのアセンブリがメイン読み込まれない[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]プロセス (w3wp.exe)。 代わりに、別のプロセス (SPUCWorkerProcess.exe) に読み込まれます。 このプロセスが監視され、クォータと制限の CPU サイクルを消費する短いループの実行などの問題を引き起こすアクティビティを実行するサンド ボックス ソリューションから、ファームの保護を実装します。  
  
## <a name="site-collection-solution-gallery"></a>サイト コレクション ソリューション ギャラリー  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]2010 は、「サイト コレクション ソリューション ギャラリー」と呼ばれる機能があります。 SharePoint 2010 サーバーの全体管理ページ、または開くことによってこの機能にアクセスすることができます、**サイトの操作** メニューを選択する**サイト設定**、選択し、**ソリューション**下にあるリンク**ギャラリー** SharePoint サイトにします。 ソリューション ギャラリーは、そのサイトのコレクションでソリューションを管理するサイト コレクションの管理者を有効にするソリューションのリポジトリです。  
  
 ソリューション ギャラリーは、SharePoint サイトのルート Web に格納されているドキュメント ライブラリです。 ソリューション ギャラリーでは、サイト テンプレートを置き換え、ソリューション パッケージをサポートします。 SharePoint ソリューション パッケージ (.wsp) ファイルがアップロードされると、サンド ボックス ソリューションとして処理されます。  
  
## <a name="sandboxed-solution-limitations"></a>サンド ボックス ソリューションの制限事項  
 サンド ボックス ソリューションの配置に使用可能な SharePoint 機能の配列がセキュリティの脆弱性を減らすために制限されます。 これらの制限事項の一部を以下に示します。  
  
-   サンド ボックス ソリューションでは、それらに使用可能なソリューションの配置可能な要素の制限されたサブセットがあります。 サイト定義し、ワークフローなどの脆弱性が潜んで SharePoint プロジェクト テンプレートは使用できません。  
  
-   SharePoint サンド ボックス ソリューションでコードを実行プロセス (SPUCWorkerProcess.exe)、main から独立した[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]アプリケーション プール (w3wp.exe) 処理します。  
  
-   マップされたフォルダーは、プロジェクトに追加できません。  
  
-   型、[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]アセンブリがサンド ボックス ソリューションで Microsoft.Office.Server は使用できません。 また、のみの種類と、[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]アセンブリが"microsoft.sharepoint"サンド ボックス ソリューションで使用できます。  
  
 指定する SharePoint ソリューション、サンド ボックス ソリューション影響を与えません。 SharePoint サーバー上にすることが重要SharePoint を SharePoint プロジェクトを展開する方法を示すのみ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]にどのようなアセンブリ バインドされているとします。 生成された .wsp ファイルには影響しません、.wsp ファイルに直接関連するデータが存在しない、*サンド ボックス ソリューション*プロパティです。  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>サンド ボックス ソリューションの機能と要素  
 サンド ボックス ソリューションは、次の機能と要素をサポートします。  
  
-   コンテンツ種類のフィールド  
  
-   カスタム アクション  
  
-   宣言型ワークフロー  
  
-   イベント レシーバー  
  
-   フィーチャーのコールアウト  
  
-   リストの定義  
  
-   インスタンスが一覧表示  
  
-   モジュール/ファイル  
  
-   ナビゲーション  
  
-   Onet.xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   派生するすべての Web パーツのサポート`System.Web.UI.WebControls.WebParts.WebPart`  
  
-   Web パーツ  
  
-   (Webtemp.xml) ではなく web テンプレート機能の要素  
  
-   視覚的 Web パーツ  
  
 サンド ボックス ソリューションは、次の機能と要素をサポートしません。  
  
-   アプリケーション ページ  
  
-   カスタム アクション グループ  
  
-   ファーム スコープの機能  
  
-   `HideCustomAction` 要素  
  
-   Web アプリケーション スコープの機能  
  
-   コードを持つワークフロー  
  
## <a name="see-also"></a>関連項目  
 [サンド ボックス間の相違点とファーム ソリューション](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
  