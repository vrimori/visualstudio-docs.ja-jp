---
title: "セキュリティ、バージョン管理、および ClickOnce の配置マニフェストの問題 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: "21"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 53f9c0114573c6f08a2d9219e4dd2028ffe9ac7c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>ClickOnce 配置でのセキュリティ、バージョン管理、およびマニフェストの問題
さまざまな問題がある[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]セキュリティ、アプリケーションのバージョン管理、およびマニフェスト構文とセマンティクスの原因となる、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]展開を成功させるされません。  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce と Windows Vista ユーザー アカウント制御  
 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]、場合でも、現在のユーザーが管理者権限を持つアカウントでログインに、既定ではアプリケーションが標準のユーザーとして実行します。 アプリケーションでは、管理者のアクセス許可を必要とするアクションを実行する必要がありますの場合は、入力をユーザーに管理者の資格情報の入力を求めるオペレーティング システムを示します。 この機能では、ユーザー アカウント制御 (UAC) の名前は、アプリケーションがユーザーの明示的な許可なくオペレーティング システム全体に影響する変更を加えるを防止します。 Windows アプリケーションの宣言を指定してこのアクセス許可の昇格が必要な`requestedExecutionLevel`属性、`trustInfo`アプリケーション マニフェストのセクションです。  
  
 により、セキュリティ昇格攻撃に対してアプリケーションを公開するリスク[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]クライアントの UAC が有効になっている場合、アプリケーションはアクセス許可の昇格を要求できません。 任意[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]設定しようとするアプリケーション、`requestedExecutionLevel`属性を`requireAdministrator`または`highestAvailable`にインストールできない[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]です。  
  
 場合によっては、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションがインストーラーの検出ロジックのための管理者権限で実行を試みる[!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]です。 この場合、設定することができます、`requestedExecutionLevel`にアプリケーション マニフェストの属性の`asInvoker`します。 これにより、アプリケーション自体が昇格せずに実行しますを。 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]すべてのアプリケーション マニフェストにこの属性が自動的に追加します。  
  
 アプリケーションの有効期間全体管理者のアクセス許可を必要とするアプリケーションを開発している場合は、代わりに Windows インストーラー (MSI) テクノロジを使用して、アプリケーションの配置を検討してください。 詳細については、次を参照してください。 [Windows インストーラーの基本概念](../extensibility/internals/windows-installer-basics.md)です。  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>オンライン アプリケーションのクォータと部分信頼アプリケーション  
 場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションが、インストールによってオンラインの代わりに実行され、オンライン アプリケーション用に確保クォータに収まる必要があります。 また、セキュリティ アクセス許可の制限付きのセットなど、部分信頼で実行されるネットワーク アプリケーションは、クォータ サイズの半分より大きいすることはできません。  
  
 詳細についてと、オンライン アプリケーションのクォータを変更する手順については、次を参照してください。 [ClickOnce キャッシュの概要](../deployment/clickonce-cache-overview.md)です。  
  
## <a name="versioning-issues"></a>バージョン管理の問題  
 問題が発生する場合は、アセンブリに厳密な名前を割り当てるし、アプリケーションの更新を反映するようにアセンブリ バージョン番号をインクリメントします。 厳密な名前のアセンブリへの参照でコンパイルされたアセンブリ自体を再コンパイルしなければ、または以前のバージョンを参照するアセンブリが試行されます。 アセンブリが、バインド要求で、古いバージョンの値を使用してこのアセンブリが試行されます。  
  
 たとえば、独自のプロジェクトのバージョンが 1.0.0.0 厳密な名前のアセンブリがあるとします。 アセンブリをコンパイルすた後には、メイン アプリケーションを含むプロジェクトへの参照として追加します。 場合は、アセンブリを更新、1.0.0.1、バージョンがインクリメントしようとするアプリケーションを再コンパイルしないで展開、アプリケーションは実行時にアセンブリを読み込むことはできません。  
  
 編集している場合にのみ、このエラーが発生することができます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]手動でマニフェストを使用して、展開を生成する場合にこのエラーを発生する必要がありますしない場合[!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)]です。  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>マニフェストで個々 の .NET Framework アセンブリを指定します。  
 アプリケーションは、手動で編集している場合の読み込みに失敗する、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]の古いバージョンを参照する展開、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]アセンブリ。 たとえばのバージョンについては、System.Net アセンブリへの参照を追加した場合、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]マニフェストで指定されたバージョンを前に、エラーが発生します。 一般に、する必要がありますを指定しない個人への参照[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]のバージョンのアセンブリ、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]に対して、アプリケーションが実行されますが、アプリケーション マニフェストで依存関係として指定されています。  
  
## <a name="manifest-parsing-issues"></a>マニフェストの解析の問題  
 マニフェスト ファイルによって使用されている[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]XML ファイルは、整形式であり有効必要があります: XML 構文規則に従います、のみ要素および関連する XML スキーマで定義されている属性を使用する必要があります。  
  
 マニフェスト ファイルで問題を引き起こす可能性のあるものは一重引用符または二重引用符などの特殊文字を含むアプリケーションの名前を選択します。 アプリケーションの名前の一部は、その[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]の id。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]現在の特殊文字の id を解析しません。 アプリケーションは、アクティブ化に失敗した場合、名のアルファベットと数字ののみを使用している、もう一度配置しようとしていることを確認します。  
  
 配置またはアプリケーション マニフェストを手動で編集した場合する可能性がありますが、意図しない破損します。 破損したマニフェストは、正しいさせない[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]インストールします。 クリックして、実行時にこのようなエラーをデバッグすることができます**詳細**上、 **ClickOnce エラー**ダイアログ ボックスで、および、ログにエラー メッセージの読み取り。 ログは、次のメッセージのいずれかの一覧に表示します。  
  
-   構文エラー、および行の数と文字の説明、エラーが発生した位置。  
  
-   要素またはマニフェストのスキーマの違反で使用される属性の名前。 マニフェストに XML を手動で追加した場合、は、マニフェストのスキーマに、追加機能を比較する必要があります。 詳細については、次を参照してください。 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)と[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)です。  
  
-   ID が競合します。 配置マニフェストとアプリケーション マニフェストで参照する依存関係は、両方で一意である必要があります、`name`と`publicKeyToken`属性。 両方の属性は、マニフェスト内で 2 つの要素間で一致、マニフェストの解析は成功しません。  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>マニフェストまたはアプリケーションを手動で変更するときの注意事項  
 アプリケーション マニフェストを更新するときに、アプリケーション マニフェストと配置マニフェストの両方を再署名する必要があります。 配置マニフェストには、そのファイルのハッシュとデジタル署名を含むアプリケーション マニフェストへの参照が含まれています。  
  
### <a name="precautions-with-deployment-provider-usage"></a>配置プロバイダーの使用に関する注意事項  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]配置マニフェストに、`deploymentProvider`プロパティからアプリケーションをインストールおよびサービスを提供する必要があります、場所の完全なパスをポイントします。  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 このパスを設定するときに[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションが作成され、インストールされているアプリケーションには必須です。 パスが、標準の場所を指している、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]インストーラーからアプリケーションと更新プログラムの検索インストールされます。 使用する場合、 **xcopy**にコピーするコマンド、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]別の場所にアプリケーションを変更せず、`deploymentProvider`プロパティ、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]も参照元の場所にダウンロードするとき、アプリケーション。  
  
 移動またはアプリケーションをコピーする場合は、更新する必要ありますも、`deploymentProvider`パス、新しい場所から実際にクライアントをインストールできるようにします。 このパスの更新はほとんどの場合、問題にアプリケーションをインストールしている場合です。 オンライン アプリケーションの設定、元の URL から常に起動される、`deploymentProvider`は省略可能です。 場合`deploymentProvider`が設定されているが有効です。 それ以外の場合、アプリケーションを起動するために使用する URL が使用ベース URL としてアプリケーション ファイルをダウンロードします。  
  
> [!NOTE]
>  マニフェストを更新するたびにする必要がありますも再度署名します。  
  
## <a name="see-also"></a>参照  
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)