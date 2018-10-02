---
title: サービス参照のトラブルシューティング |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f6d9510bf667b95dde4619f469b51041c07c0b4e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548958"
---
# <a name="troubleshooting-service-references"></a>サービス参照のトラブルシューティング
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[サービス参照のトラブルシューティング](https://docs.microsoft.com/visualstudio/data-tools/troubleshooting-service-references)します。

このトピックで使用している場合に発生する一般的な問題[!INCLUDE[vsindigo](../includes/vsindigo-md.md)]または[!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]参照[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。

## <a name="error-returning-data-from-a-service"></a>サービスからデータを返すときのエラー
 戻ると、`DataSet`または`DataTable`、サービスから「受信メッセージの最大サイズ クォータを超えました」例外が発生する可能性があります。 既定で、`MaxReceivedMessageSize`一部のバインドのプロパティは、サービス拒否攻撃に対する露出を制限する比較的小さい値に設定されています。 例外を回避するには、この値を増やすことができます。

 このエラーを修復するには:

1.  **ソリューション エクスプ ローラー**、app.config ファイルを開く をダブルクリックします。

2.  検索、`MaxReceivedMessageSize`プロパティより大きい値に変更します。

## <a name="cannot-find-a-service-in-my-solution"></a>ソリューションでサービスを検索することはできません。
 クリックすると、 **Discover**ボタン、**サービス参照の追加**ダイアログ ボックスで、サービスの一覧で、ソリューション内の 1 つまたは複数の WCF サービス ライブラリ プロジェクトは表示されません。 これは、サービス ライブラリは、ソリューションに追加されましたが、まだコンパイルされていない場合に発生することができます。

 このエラーを修復するには:

-   **ソリューション エクスプ ローラー**WCF サービス ライブラリ プロジェクトを右クリックし、クリックして、**ビルド**します。

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>リモート デスクトップ経由でサービスへのアクセス エラー
 ユーザーがアクセスするときに、リモート デスクトップ接続と、ユーザーを Web でホストされる WCF サービスには、管理者のアクセス許可がありません、NTLM 認証が使用されます。 ユーザーが次のエラー メッセージを受け取ることがあります、ユーザーは、管理者のアクセス許可を持っていない場合:"HTTP 要求はクライアントの認証方式 'Anonymous' で承認されていません。 サーバーから受信した認証ヘッダーが 'NTLM'。"

 このエラーを修復するには:

1.  Web サイト プロジェクトで開き、**プロパティ**ページ。

2.  **開始オプション**タブで、、 **NTLM 認証**チェック ボックスをオンします。

    > [!NOTE]
    > Web サイト専用の WCF サービスが含まれている場合、NTLM 認証をオフにする必要があります。 WCF サービスのセキュリティは、web.config ファイルの構成によって管理されます。 これにより、NTLM 認証が不要にします。

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>生成されたクラスのアクセス レベルの設定が影響を与えません
 設定、**アクセス レベルが生成されたクラスの**オプション、**サービス参照の構成**ダイアログ ボックスを**内部**または**フレンド**常に機能しません。 アクセス レベルを持つ場合でも、ダイアログ ボックスで設定するオプションが表示されたら、結果として得られるサポート クラスが生成されます`Public`します。

 これは、特定の型を使用してシリアル化などの既知の制限事項、<xref:System.Xml.Serialization.XmlSerializer>します。

## <a name="error-debugging-service-code"></a>サービス コードのデバッグ エラー
 クライアント コードから、WCF サービスのコードにステップ インすると、シンボルが見つからないことに関するエラーが表示される可能性があります。 これは、ソリューションの一部であったサービスが移動または、ソリューションから削除されるときに発生します。

 最初に現在のソリューションの一部となっている WCF サービスへの参照を追加すると、サービス プロジェクトとサービスのクライアント プロジェクトの明示的なビルドの依存関係が追加されます。 これは、クライアント常にアクセスする最新の状態のサービスのバイナリ、クライアント コードからサービスのコードにステップ インなどのシナリオのデバッグにとって特に重要なことを保証します。

 サービス プロジェクトをソリューションから削除する場合、この明示的なビルド依存関係は無効になります。 Visual Studio を保証できなくサービス プロジェクトが再構築を必要に応じて。

 このエラーを解決するには、手動でサービス プロジェクトを再構築が必要。

1.  **[ツール]** メニューの **[オプション]** をクリックします。

2.  **オプション**] ダイアログ ボックスで、展開**プロジェクトおよびソリューション**、し、[**全般**します。

3.  確認します、**ビルド構成の詳細を表示** チェック ボックスが選択されているし、クリックして**OK**。

4.  WCF サービス プロジェクトを読み込みます。 詳細については、次を参照してください。 [NIB How to: マルチ プロジェクト ソリューションの作成](http://msdn.microsoft.com/en-us/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)です。

5.  **Configuration Manager**ダイアログ ボックスで、セット、**アクティブ ソリューション構成**に**デバッグ**します。 詳細については、「[How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md)」(方法 : 構成を作成および編集する) を参照してください。

6.  **ソリューション エクスプ ローラー**、WCF サービス プロジェクトを選択します。

7.  **ビルド** メニューのをクリックして**リビルド**WCF サービス プロジェクトをリビルドします。

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services は、ブラウザーには表示しません。
 内のデータの XML 表現を表示しようとするときに、 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]、Internet Explorer に RSS フィードとしてデータが誤って解釈可能性があります。 RSS フィードを表示するオプションが無効になっていることを確認してください。

 このエラーを修正するのには、RSS フィードを無効にします。

1.  Internet Explorer で、上、**ツール** メニューのをクリックして**インターネット オプション**します。

2.  **コンテンツ**] タブで、**フィード**セクションで、[**設定**します。

3.  **フィードの設定**、ダイアログ ボックスをオフ、**フィードの読み取りビューで有効にする**チェック ボックスをオンにして**OK**。

4.  をクリックして**OK**を閉じる、**インターネット オプション** ダイアログ ボックス。

## <a name="see-also"></a>関連項目

- [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)