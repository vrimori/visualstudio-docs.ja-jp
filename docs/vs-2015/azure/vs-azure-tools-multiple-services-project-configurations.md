---
title: 複数のサービス構成を使用して Azure プロジェクトの構成 |Microsoft Docs
description: ServiceDefinition.csdef、ServiceConfiguration.Local.cscfg および ServiceConfiguration.Cloud.cscfg ファイルを変更して、Azure クラウド サービス プロジェクトを構成する方法について説明します。
author: ghogen
manager: douge
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: f309c2a960d011601a9fdd41e29d767c667de838
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002932"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>複数のサービス構成を使用するための Visual Studio での Azure プロジェクトの構成

Visual Studio での Azure クラウド サービス プロジェクトには、次の 3 つの構成ファイルが含まれています: `ServiceDefinition.csdef`、 `ServiceConfiguration.Local.cscfg`、および`ServiceConfiguration.Cloud.cscfg`:

- `ServiceDefinition.csdef` クラウド サービスとそのロールの要件を記述して、すべてのインスタンスに適用される設定を提供する Azure にデプロイされます。 設定は、Azure サービス ホスト ランタイム API を使用して実行時に読み込むことができます。 このファイルは、クラウド サービスが停止している場合にのみ、Azure で更新できます。
- `ServiceConfiguration.Local.cscfg` `ServiceConfiguration.Cloud.cscfg`ファイルし、各ロールに対して実行するインスタンスの数を指定の定義内の設定の値を指定します。 「ローカル」ファイルには、ローカル デバッグに使用される値が含まれています。「クラウド」ファイルとして Azure にデプロイされた`ServiceConfiguration.cscfg`し、サーバー環境の設定を提供します。 Azure でクラウド サービスの実行中に、このファイルを更新できます。

構成設定の管理し、の適切なロールのプロパティ ページを使用して Visual Studio で変更 (ロールを右クリックして**プロパティ**、またはロールをダブルクリックします)。 変更をスコープでは、どの構成を選択してください。、**サービス構成**ドロップダウンします。 Web および worker ロールのプロパティは似ています、を除き、次のセクションで説明します。

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

サービス定義ファイルとサービス構成ファイルの基になるスキーマについては、次を参照してください。、 [.csdef XML スキーマ](/azure/cloud-services/schema-csdef-file.md)と[.cscfg XML スキーマ](/azure/cloud-services/schema-cscfg-file.md)記事。 サービス構成の詳細については、次を参照してください。 [Cloud Services の構成方法](/azure/cloud-services/cloud-services-how-to-configure-portal)します。


## <a name="configuration-page"></a>[構成] ページ

### <a name="service-configuration"></a>サービス構成

Select を`ServiceConfiguration.*.cscfg`ファイルは変更の影響を受けません。 既定では、ローカルとクラウドのバリエーションと、使用することができます、**管理しています.** コピー、名前の変更、および構成ファイルを削除するコマンド。 これらのファイルがクラウド サービス プロジェクトに追加されに表示されます**ソリューション エクスプ ローラー**します。 ただし、名前変更や構成の削除は、このコントロールからのみ実行できます。

### <a name="instances"></a>インスタンス

設定、**インスタンス**プロパティをこのロールに対して、サービスが実行するインスタンスの数をカウントします。

設定、 **VM サイズ**プロパティを**極小**、**小さな**、 **Medium**、 **Large**、または**超大規模な**します。  詳細については、次を参照してください。 [Cloud Services のサイズ](/azure/cloud-services/cloud-services-sizes-specs)します。

### <a name="startup-action-web-role-only"></a>スタートアップ アクション (Web ロールのみ)

Visual Studio はデバッグを開始するときに、HTTP エンドポイントまたは HTTPS エンドポイントで、あるいはその両方の web ブラウザーを起動する必要がありますを指定するには、このプロパティを設定します。

**HTTPS エンドポイント**オプションは、ロールの HTTPS エンドポイントを既に定義した場合にのみ使用できます。 HTTPS エンドポイントを定義することができます、**エンドポイント**プロパティ ページ。

HTTPS エンドポイントを既に追加した場合は、HTTPS エンドポイント オプションが既定で有効にし、デバッグの開始し、HTTP エンドポイント用のブラウザーだけでなく両方のスタートアップ オプションが有効になっていると仮定すると、Visual Studio がこのエンドポイントでブラウザーを起動します。

### <a name="diagnostics"></a>診断

既定では、診断は、Web ロールに対して有効です。 ローカル ストレージ エミュレーターを使用する Azure クラウド サービス プロジェクトとストレージ アカウントが設定されます。 Azure にデプロイする準備ができたら、ビルダーのボタンを選択することができます (**.**) 代わりに Azure storage を使用します。 オンデマンドまたは自動的にスケジュールされた間隔では、ストレージ アカウントに診断データを転送できます。 Azure 診断の詳細については、次を参照してください。 [Enabling diagnostics in Azure Cloud Services および仮想マシン診断](/azure/cloud-services/cloud-services-dotnet-diagnostics)します。

## <a name="settings-page"></a>設定 ページ

**設定** ページで、名前と値のペアとしての構成に設定を追加することができます。 ロールで実行されるコードが提供するクラスを使用して実行時に、構成設定の値を読み取ることができます、 [Azure マネージ ライブラリ](http://go.microsoft.com/fwlink?LinkID=171026)、特に、 [GetConfigurationSettingValue](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.getconfigurationsettingvalue.aspx)メソッド。

### <a name="configuring-a-connection-string-for-a-storage-account"></a>ストレージ アカウントの接続文字列を構成します。

接続文字列は、ストレージ エミュレーターまたは Azure storage アカウントに接続および認証情報を提供する設定です。 ロール内のコードが Azure storage (blob、キュー、またはテーブル) にアクセスするたびに、接続文字列が必要です。

> [!Note]
> Azure ストレージ アカウントの接続文字列は、定義された形式を使用する必要があります (を参照してください[Azure Storage 接続文字列を構成](/azure/storage/common/storage-configure-connection-string))。

Azure ストレージ アカウントを設定、アプリケーションをデプロイするときに、必要に応じて、ローカル ストレージを使用する接続文字列には、クラウド サービスを設定できます。 接続文字列を正しく設定に失敗したが、ロールを開始するに設定したり、初期化、ビジー状態、停止の状態を順番にあります。

接続文字列を作成するには、選択**設定の追加**設定と**型**「接続文字列」にします。

新規または既存の接続文字列の場合は、次のように選択します **.。*** の右側で、**値**フィールドを開く、**ストレージ接続文字列の作成**ダイアログ。

1. **を使用して接続**、選択、**サブスクリプション**サブスクリプションからストレージ アカウントを選択することです。 Visual Studio から自動的にストレージ アカウントの資格情報を取得し、`.publishsettings`ファイル。
1. 選択**資格情報を手動で入力された**使用アカウント名を指定して、Azure portal からの情報を使用して直接キーします。 アカウント キーをコピーするには。
    1. ポータルで選択し、azure ストレージ アカウントに移動**キーの管理**します。
    1. アカウント キーをコピーするには、Azure ポータルで、ストレージ アカウントに移動します。**設定 > アクセス キー**、プライマリ アクセス キーをクリップボードにコピーするコピー ボタンを使用します。
1. 接続オプションのいずれかを選択します。 **カスタム エンドポイントの指定**blob、テーブル、特定の Url を指定することを確認し、キューに入れます。 カスタム エンドポイントを使用することが可能[カスタム ドメイン](/azure/storage/blobs/storage-custom-domain-name.md)とアクセスをより正確に制御します。 参照してください[Azure ストレージ接続文字列を構成する](/azure/storage/common/storage-configure-connection-string)します。
1. 選択**OK**、し**ファイル > 保存**新しい接続文字列で構成を更新します。

ここでも、アプリケーションを Azure に発行するときは、Azure ストレージ アカウント接続文字列を含むサービス構成を選択します。 アプリケーションを発行すると後、は、アプリケーションが Azure ストレージ サービスに対して期待どおりに動作することを確認します。

サービス構成を更新する方法の詳細については、セクションをご覧ください。[ストレージ アカウントの接続文字列の管理](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts)します。

## <a name="endpoints-page"></a>[エンドポイント] ページ

Web ロールでは、1 つの HTTP エンドポイントがポート 80 で通常があります。 一方で、ワーカー ロールでは、HTTP、HTTPS、または TCP エンドポイントの任意の数を持つことができます。 エンドポイントには、外部クライアントに提供するには、入力エンドポイントは、またはサービスで実行されているその他のロールが使用できるは、内部エンドポイントを指定できます。

- HTTP エンドポイントを外部クライアントおよび Web ブラウザーを使用できるようにするには、入力エンドポイントの種類を変更し、名前およびパブリック ポート番号を指定します。
- HTTPS エンドポイントを外部クライアントおよび Web ブラウザーを使用できるようにするにエンドポイントの種類を変更**入力**名前、パブリック ポート番号、および管理証明書の名前を指定します。 証明書を定義することも必要があります、**証明書**管理証明書を指定する前に、プロパティ ページ。 
- その他のクラウド サービス ロールでエンドポイントを内部利用できるように、内部エンドポイントの種類を変更し、名前と、このエンドポイントの使用可能なプライベート ポートを指定します。

## <a name="local-storage-page"></a>ローカル ストレージ ページ

使用することができます、**ローカル ストレージ**ロールの 1 つまたは複数のローカル ストレージ リソースを予約する プロパティ ページ。 ローカル ストレージ リソースは、ロールのインスタンスが実行されている Azure の仮想マシンのファイル システムで予約されたディレクトリです。

## <a name="certificates-page"></a>証明書 ページ

**証明書**プロパティ ページをサービスの構成については、証明書を追加します。 証明書は、サービスをパッケージ化されないことに注意してください。経由で Azure に証明書を個別にアップロードする必要があります、 [Azure portal](http://portal.azure.com)します。

ここで、証明書を追加すると、サービス構成に、証明書についての情報が追加されます。 証明書は、サービスでパッケージ化されません。Azure portal を介して個別に、証明書をアップロードする必要があります。

証明書とロールに関連付けるには、証明書の名前を提供します。 この名前を使用して、HTTPS エンドポイントを構成する場合、証明書を参照する、**エンドポイント**ページ。 次に、証明書ストアがかどうかを指定**ローカル マシン**または**現在のユーザー**とストアの名前。 最後に、証明書の拇印を入力します。 Current user \personal (My) ストアの証明書が、表示されたリストから証明書を選択して、証明書の拇印を入力できます。 その他の場所に存在する場合は、手動で拇印の値を入力します。

証明書ストアから証明書を追加すると、すべての中間証明書は自動的に構成設定に追加します。 さらに、これらの中間証明書は、SSL に対してサービスを正しく構成する Azure にアップロードする必要があります。

サービスに関連付けた管理証明書は、クラウドで実行されている場合にのみ、サービスに適用されます。 サービスは、ローカル開発環境で実行中は、コンピューティング エミュレーターによって管理されている標準の証明書を使用します。
