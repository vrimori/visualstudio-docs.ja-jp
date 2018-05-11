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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c244489f21dec3783aed9d970b46805d204a1104
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshoot-service-references"></a>サービス参照をトラブルシューティングします。

このトピックでは、Windows Communication Foundation (WCF) または Visual Studio での WCF Data Services の参照を使用する場合に発生する一般的な問題を示します。

## <a name="error-returning-data-from-a-service"></a>サービスからデータを返すときのエラー

戻るとき、`DataSet`または`DataTable`サービスから「受信メッセージの最大サイズ クォータを超えました」例外が発生する可能性があります。 既定では、`MaxReceivedMessageSize`一部のバインドのプロパティがサービス拒否攻撃への露出を制限する比較的小さな値に設定します。 例外を防ぐためにこの値を大きくことができます。 詳細については、「<xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>」を参照してください。

このエラーを修復するには:

1.  **ソリューション エクスプ ローラー**、app.config ファイルを開くをダブルクリックします。

2.  検索、`MaxReceivedMessageSize`プロパティより大きい値に変更します。

## <a name="cannot-find-a-service-in-my-solution"></a>ソリューションでサービスを見つけることができません。

クリックすると、 **Discover**ボタンをクリックして、**サービス参照の追加**ダイアログ ボックスで、サービスの一覧で、ソリューション内の 1 つまたは複数の WCF サービス ライブラリ プロジェクトは表示されません。 これは、サービス ライブラリは、ソリューションに追加されましたが、まだコンパイルされていない場合に発生することができます。

このエラーを修復するには:

-   **ソリューション エクスプ ローラー**を WCF サービス ライブラリ プロジェクトを右クリックし、をクリックして**ビルド**です。

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>リモート デスクトップ経由でサービスへのアクセス エラー

ユーザーがアクセスするときに、Web でホストされる WCF サービス経由でリモート デスクトップ接続と、ユーザーには、管理アクセス許可がありません、NTLM 認証を使用します。 ユーザーが管理者権限を持っていない場合、ユーザーは、次のエラー メッセージを受け取ります可能性があります:"HTTP 要求はクライアントの認証方式 'Anonymous' で承認されていません。 サーバーから受信した認証ヘッダーは NTLM でした。"

このエラーを修復するには:

1.  Web サイト プロジェクトで開き、**プロパティ**ページ。

2.  **開始オプション**タブで、、 **NTLM 認証**チェック ボックスをオンします。

    > [!NOTE]
    > NTLM 認証の排他的 WCF サービスを含む Web サイトでのみ無効にする必要があります。 WCF サービスのセキュリティは、web.config ファイルで構成を通じて管理されます。 これにより、NTLM 認証が不要にします。

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>生成されたクラスのアクセス レベルの設定が影響を与えません

設定、**アクセス レベルが生成されたクラスの**オプション、**サービス参照の構成**ダイアログ ボックスを**内部**または**フレンド**常に動作しません。 アクセス レベルの結果として得られるサポート クラスが生成された場合でも、ダイアログ ボックスで設定するオプションが表示されたら、`Public`です。

これは、特定の型を使用してシリアル化などの既知の制限事項、<xref:System.Xml.Serialization.XmlSerializer>です。

## <a name="error-debugging-service-code"></a>サービス コードのデバッグ エラー

クライアント コードから、WCF サービスのコードにステップ インすると、シンボルが見つからないことに関するエラーが表示される可能性があります。 これは、ソリューションの一部であったサービスが移動またはソリューションから削除されたときに発生します。

最初に、現在のソリューションに含まれている WCF サービスへの参照を追加すると、サービス プロジェクトとサービス クライアント プロジェクト間で、明示的なビルドの依存関係が追加されます。 これにより、クライアント常にアクセスする最新のサービスのバイナリはデバッグ サービス コードに、クライアント コードからステップ実行などのシナリオで特に重要です。

サービス プロジェクトをソリューションから削除する場合、この明示的なビルドの依存関係は無効になります。 Visual Studio 保証できなくサービス プロジェクトを再構築を必要に応じて。

このエラーを解決するには、手動でサービス プロジェクトを再構築が必要。

1.  **[ツール]** メニューの **[オプション]** をクリックします。

2.  **オプション**] ダイアログ ボックスで、展開**プロジェクトおよびソリューション**、し、[**全般**です。

3.  確認して、 **Show advanced ビルド構成** チェック ボックスを選択して、をクリックして**OK**です。

4.  WCF サービス プロジェクトを読み込みます。

5.  **Configuration Manager**ダイアログ ボックスで、設定、**アクティブ ソリューション構成**に**デバッグ**です。 詳細については、「[How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md)」(方法 : 構成を作成および編集する) を参照してください。

6.  **ソリューション エクスプ ローラー**、WCF サービス プロジェクトを選択します。

7.  **ビルド** メニューのをクリックして**を再構築**を WCF サービス プロジェクトをリビルドします。

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services は、ブラウザーで表示されません。

内のデータの XML 表現を表示しようとするときに、 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]、Internet Explorer に RSS フィードとしてデータが誤って解釈可能性があります。 RSS フィードを表示するオプションは無効になっていることを確認します。

このエラーを修正するのには、RSS フィードを無効にします。

1.  Internet Explorer で、上、**ツール** メニューのをクリックして**インターネット オプション**です。

2.  **コンテンツ**] タブで、**フィード**セクションで、[**設定**です。

3.  **フィードの設定**ダイアログ ボックスで、クリア、**フィードの読み取りビューを有効に**チェック ボックスをクリックして **[ok]** です。

4.  をクリックして**OK**を閉じる、**インターネット オプション** ダイアログ ボックス。

## <a name="see-also"></a>関連項目

- [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)