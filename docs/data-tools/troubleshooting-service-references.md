---
title: サービス参照のトラブルシューティング
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 573019483f1c7c616f8bdf61286c46f76458354f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031289"
---
# <a name="troubleshoot-service-references"></a>サービス参照をトラブルシューティングする

このトピックでは、Windows Communication Foundation (WCF) または Visual Studio での WCF Data Services 参照を使用している場合に発生する一般的な問題を一覧表示します。

## <a name="error-returning-data-from-a-service"></a>サービスからデータを返すときのエラー

戻ると、`DataSet`または`DataTable`、サービスから「受信メッセージの最大サイズ クォータを超えました」例外が発生する可能性があります。 既定で、`MaxReceivedMessageSize`一部のバインドのプロパティは、サービス拒否攻撃に対する露出を制限する比較的小さい値に設定されています。 例外を回避するには、この値を増やすことができます。 詳細については、「<xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>」を参照してください。

このエラーを修復するには:

1.  **ソリューション エクスプ ローラー**、ダブルクリックして、 *app.config*ファイルを開きます。

2.  検索、`MaxReceivedMessageSize`プロパティより大きい値に変更します。

## <a name="cannot-find-a-service-in-my-solution"></a>ソリューションでサービスを検索することはできません。

クリックすると、 **Discover**ボタン、**サービス参照の追加**ダイアログ ボックスで、サービスの一覧で、ソリューション内の 1 つまたは複数の WCF サービス ライブラリ プロジェクトは表示されません。 これは、サービス ライブラリは、ソリューションに追加されましたが、まだコンパイルされていない場合に発生することができます。

このエラーを修復するには:

-   **ソリューション エクスプ ローラー**WCF サービス ライブラリ プロジェクトを右クリックし、クリックして、**ビルド**します。

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>リモート デスクトップ経由でサービスへのアクセス エラー

ユーザーがアクセスするときに、リモート デスクトップ接続と、ユーザーを Web でホストされる WCF サービスには、管理者のアクセス許可がありません、NTLM 認証が使用されます。 ユーザーが管理者のアクセス許可を持たない場合、ユーザーは、次のエラー メッセージを受信可能性があります。"HTTP 要求はクライアントの認証方式 'Anonymous' で承認されていません。 サーバーから受信した認証ヘッダーが 'NTLM'。"

このエラーを修復するには:

1.  Web サイト プロジェクトで開き、**プロパティ**ページ。

2.  **開始オプション**タブで、、 **NTLM 認証**チェック ボックスをオンします。

    > [!NOTE]
    > 排他的 WCF サービスが含まれている web サイトだけで NTLM 認証をオフにする必要があります。 WCF サービスのセキュリティは構成を通じて管理、 *web.config*ファイル。 これにより、NTLM 認証が不要にします。

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>生成されたクラスの設定のアクセス レベルが影響を与えません

設定、**アクセス レベルが生成されたクラスの**オプション、**サービス参照の構成**ダイアログ ボックスを**内部**または**フレンド**常に機能しません。 アクセス レベルの結果として得られるサポート クラスが生成される場合でも、ダイアログ ボックスで設定するオプションが表示されたら、`Public`します。

これは、特定の型を使用してシリアル化などの既知の制限事項、<xref:System.Xml.Serialization.XmlSerializer>します。

## <a name="error-debugging-service-code"></a>サービス コードのデバッグ エラー

クライアント コードから、WCF サービスのコードにステップ インすると、シンボルが見つからないことに関するエラーが表示される可能性があります。 これは、ソリューションの一部であったサービスが移動または、ソリューションから削除されるときに発生します。

最初に現在のソリューションの一部となっている WCF サービスへの参照を追加すると、サービス プロジェクトとサービスのクライアント プロジェクトの明示的なビルドの依存関係が追加されます。 これにより、クライアント常にアクセスする最新のサービスのバイナリはクライアント コードからサービスのコードにステップ インなどのシナリオのデバッグに特に重要です。

サービス プロジェクトをソリューションから削除する場合、この明示的なビルド依存関係は無効になります。 Visual Studio を保証できなくサービス プロジェクトがリビルドされるに応じて。

このエラーを解決するには、手動でサービス プロジェクトを再構築が必要。

1.  **[ツール]** メニューの **[オプション]** をクリックします。

2.  **オプション**] ダイアログ ボックスで、展開**プロジェクトおよびソリューション**、し、[**全般**します。

3.  確認します、**ビルド構成の詳細を表示** チェック ボックスが選択されているし、クリックして**OK**。

4.  WCF サービス プロジェクトを読み込みます。

5.  **Configuration Manager**ダイアログ ボックスで、セット、**アクティブ ソリューション構成**に**デバッグ**します。 詳細については、「[方法 :構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)」を参照してください。

6.  **ソリューション エクスプ ローラー**、WCF サービス プロジェクトを選択します。

7.  **ビルド** メニューのをクリックして**リビルド**WCF サービス プロジェクトをリビルドします。

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services は、ブラウザーには表示しません。

内のデータの XML 表現を表示しようとするときに、 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]、Internet Explorer に RSS フィードとしてデータが誤って解釈可能性があります。 RSS フィードを表示するオプションが無効になっていることを確認します。

このエラーを修正するのには、RSS フィードを無効にします。

1.  Internet Explorer で、**[ツール]** メニューの **[インターネット オプション]** をクリックします。

2.  **コンテンツ**] タブで、**フィード**セクションで、[**設定**します。

3.  **フィードの設定**、ダイアログ ボックスをオフ、**フィードの読み取りビューで有効にする**チェック ボックスをオンにして**OK**。

4.  をクリックして**OK**を閉じる、**インターネット オプション** ダイアログ ボックス。

## <a name="see-also"></a>関連項目

- [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)