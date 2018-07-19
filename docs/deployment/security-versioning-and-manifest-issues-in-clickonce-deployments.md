---
title: セキュリティ、バージョン管理、および ClickOnce 配置マニフェストの問題 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7ae835b53960ca6952b71c10a2348f707785e16
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081746"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>セキュリティ、バージョン管理、および ClickOnce 配置マニフェストの問題

さまざまな問題がある[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]セキュリティ、アプリケーションのバージョン管理とマニフェストの構文およびセマンティクスの原因となる、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開が失敗します。

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce と Windows Vista ユーザー アカウント制御

[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]、場合でも、現在のユーザーが管理者のアクセス許可のあるアカウントでログインしているが標準ユーザーは、既定でアプリケーションを実行します。 アプリケーションでは、管理者のアクセス許可が必要なアクションを実行する必要がある場合は、ユーザーに管理者の資格情報の入力を求められますし、オペレーティング システムが通知されます。 この機能は、ユーザー アカウント制御 (UAC) の名前には、ユーザーの明示的な承認なくオペレーティング システム全体に影響する変更を行うアプリケーションができないようにします。 Windows アプリケーションは、指定することで、このアクセス許可の昇格を必要があることを宣言、`requestedExecutionLevel`属性、`trustInfo`アプリケーション マニフェストのセクション。

セキュリティの昇格攻撃にアプリケーションを公開するリスクのため[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]クライアントの UAC が有効になっている場合、アプリケーションがアクセス許可の昇格を要求できません。 任意[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]設定しようとするアプリケーションの`requestedExecutionLevel`属性を`requireAdministrator`または`highestAvailable`にインストールできない[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]します。

場合によってで、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]インストーラー検出ロジックのための管理者権限で実行するアプリケーションを試みる可能性があります[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]します。 この場合、設定することができます、`requestedExecutionLevel`属性にアプリケーション マニフェストで`asInvoker`します。 これは、結果、アプリケーション自体を昇格なしでも実行します。 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] すべてのアプリケーション マニフェストにこの属性が自動的に追加します。

アプリケーションの有効期間にわたって管理者のアクセス許可を必要とするアプリケーションを開発している場合は、代わりに Windows インストーラー (MSI) テクノロジを使用して、アプリケーションの配置を検討してください。 詳細については、次を参照してください。 [Windows インストーラーの基本事項](../extensibility/internals/windows-installer-basics.md)します。

## <a name="online-application-quotas-and-partial-trust-applications"></a>オンライン アプリケーションのクォータと部分信頼アプリケーション

場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションがインストールからオンラインの代わりに実行され、オンライン アプリケーション用に確保クォータ内に収まるようにする必要があります。 また、制限された一連のセキュリティのアクセス許可など、部分信頼で実行するネットワーク アプリケーションは、クォータ サイズの半分よりも大きいすることはできません。

詳細については、および手順については、オンライン アプリケーションのクォータを変更する方法については、次を参照してください。 [ClickOnce キャッシュの概要](../deployment/clickonce-cache-overview.md)します。

## <a name="versioning-issues"></a>バージョン管理の問題

アプリケーションの更新プログラムを反映するようにアセンブリ バージョン番号をインクリメントし、アセンブリに厳密な名前を割り当てる場合、問題が発生する可能性があります。 厳密な名前のアセンブリへの参照でコンパイルされたアセンブリ自体を再コンパイルしなければ、または以前のバージョンを参照するアセンブリを試みます。 アセンブリが、バインド要求で古いバージョンの値を使用するため、このアセンブリが試行されます。

たとえば、バージョン 1.0.0.0 と独自のプロジェクトで厳密な名前のアセンブリがあるとします。 アセンブリをコンパイルした後、メインのアプリケーションを含むプロジェクトへの参照として追加します。 バージョンを 1.0.0.1、インクリメント、アプリケーションを再コンパイルしないでデプロイしようし、アセンブリを更新、アプリケーションは実行時にアセンブリを読み込むことはできません。

編集する場合にのみ、このエラーが発生することができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]マニフェストに手動で Visual Studio を使用してデプロイを生成する場合にいないこのエラーが発生する必要があります。

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>マニフェストで個々 の .NET Framework アセンブリを指定します。

アプリケーションの手動で編集した場合の読み込みに失敗、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]の以前のバージョンを参照する展開を[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]アセンブリ。 バージョンの System.Net アセンブリへの参照を追加した場合など、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]マニフェストで指定されたバージョンを前に、エラーが発生します。 個人への参照を指定しないで一般に、する[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]のバージョンと、アセンブリ、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]に対してアプリケーションを実行するアプリケーション マニフェストで依存関係として指定されます。

## <a name="manifest-parsing-issues"></a>マニフェストの解析の問題

マニフェスト ファイルで使用される[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]XML ファイル、および整形式で有効なの両方があります:、XML 構文規則に従うし、要素および関連する XML スキーマで定義されている属性のみを使用する必要があります。

マニフェスト ファイルで問題を引き起こす可能性のあるものは単一引用符または二重引用符などの特殊文字を含む、アプリケーションの名前を選択します。 アプリケーションの名前の一部は、その[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]の id。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 現在の id に特殊文字を解析しません。 アクティブ化するアプリケーションが失敗した場合、名前のアルファベットと数字ののみを使用している、もう一度デプロイしようとするを確認します。

配置またはアプリケーション マニフェストを手動で編集した場合を意図せず壊れていること。 正しいにより、破損したマニフェスト[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]インストールします。 クリックして、実行時にこのようなエラーをデバッグすることができます**詳細**上、 **ClickOnce エラー**ダイアログ ボックスで、およびログにエラー メッセージを読み取っています。 ログは、次のメッセージのいずれかの一覧に表示します。

- 構文エラー、および行の数と文字の説明、エラーが発生した位置。

- 要素またはマニフェストのスキーマの違反で使用される属性の名前。 場合は、マニフェストに XML を手動で追加した、マニフェストのスキーマに、追加機能を比較する必要があります。 詳細については、次を参照してください。 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)と[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)します。

- ID が競合します。 配置マニフェストとアプリケーション マニフェストで参照する依存関係は、両方で一意である必要があります、`name`と`publicKeyToken`属性。 両方の属性は、マニフェスト内で 2 つの要素間で一致、マニフェストの解析は成功しません。

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>マニフェストまたはアプリケーションを手動で変更するときの注意事項

アプリケーション マニフェストを更新するときに、アプリケーション マニフェストと配置マニフェストの両方を再署名する必要があります。 配置マニフェストには、そのファイルのハッシュとデジタル署名を含むアプリケーション マニフェストへの参照が含まれています。

### <a name="precautions-with-deployment-provider-usage"></a>配置プロバイダーの使用に関する注意事項

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェスト、`deploymentProvider`アプリケーションをインストールおよびサービスを提供する必要がありますから場所の完全なパスを指すプロパティ。

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

場合、このパスが設定[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションが作成され、インストールされているアプリケーションには必須です。 パスが標準の場所を指している、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]インストーラーからアプリケーションと更新プログラムの検索、インストールされます。 使用する場合、 **xcopy**コマンドをコピーする、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]別の場所にアプリケーションは変更しないでください、`deploymentProvider`プロパティ、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]でも参照元の場所にダウンロードするとき、アプリケーション。

更新する必要があるアプリケーションをコピーまたは移動する場合、`deploymentProvider`パス、新しい場所から実際にクライアントをインストールできるようにします。 このパスを更新すると、アプリケーションをインストールしている場合にほとんどの場合に問題です。 設定元の URL から起動される常にオンライン アプリケーションの`deploymentProvider`は省略可能です。 場合`deploymentProvider`設定が受け入れられますはそれ以外の場合、アプリケーションを起動するための URL として使用するベース URL をアプリケーション ファイルをダウンロードします。

> [!NOTE]
> マニフェストを更新するたびにする必要がありますも再度署名します。

## <a name="see-also"></a>関連項目

[ClickOnce 配置をトラブルシューティングします。](../deployment/troubleshooting-clickonce-deployments.md)  
[Securw ClickOnce アプリケーション](../deployment/securing-clickonce-applications.md)  
[ClickOnce 配置ストラテジを選択します。](../deployment/choosing-a-clickonce-deployment-strategy.md)