---
title: Office ソリューションに信頼を付与
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b07aea10d2b1d55e98239d6dd804a506390f1974
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871378"
---
# <a name="grant-trust-to-office-solutions"></a>Office ソリューションに信頼を付与
  ソリューションのアセンブリ、アプリケーション マニフェスト、配置マニフェスト、およびドキュメントを信頼する Office ソリューションは各ターゲット コンピューターのセキュリティ ポリシーを変更する信頼を付与します。 ユーザーまたはエンドユーザーによって、Office ソリューションに信頼を付与できます。

 Office ソリューションに完全な信頼を付与するには、アプリケーションと配置マニフェストに署名します。

 Office ソリューションに信頼を付与で信頼の決定を行うエンドユーザー、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信頼プロンプト。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

##  <a name="Signing"></a> アプリケーションと配置マニフェストに署名することで、ソリューションを信頼します。
 すべてのアプリケーションと展開マニフェスト Office ソリューションは、パブリッシャーを識別する証明書で署名する必要があります。 証明書は、信頼の決定を行うための基礎を提供します。

 一時的な証明書が作成され、デバッグしながらソリューションを実行するために、ビルド時に信頼を付与します。 一時的な証明書で署名されたソリューションを発行する場合、エンドユーザーは信頼の決定を求めます。

 既知の信頼された証明書を使用して、ソリューションに署名する場合、ソリューションは信頼の決定にエンド ユーザーに確認しないで自動的にインストールされます。 署名証明書を取得する方法の詳細については、次を参照してください。 [ClickOnce と Authenticode](../deployment/clickonce-and-authenticode.md)します。 証明書を取得した後、信頼された発行元一覧に追加して、証明書を明示的に信頼する必要があります。 詳細については、「[方法 :ClickOnce アプリケーションのクライアント コンピューターに信頼された発行元を追加](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)します。

 場合は、開発者が一時的な証明書を使用して、ソリューションと、管理者が再署名既知の信頼された証明書を使用したカスタマイズ マニフェストの生成および編集ツールを使用して (*mage.exe*) のいずれかである、Microsoft .NET Framework のツールです。 ソリューションの署名の詳細については、次を参照してください。[方法。Office ソリューションに署名](../vsto/how-to-sign-office-solutions.md)と[方法。アプリケーション マニフェストおよび配置マニフェストに署名する](../ide/how-to-sign-application-and-deployment-manifests.md)」を参照してください。

##  <a name="TrustPrompt"></a>ClickOnce 信頼プロンプトを使用してソリューションを信頼します。
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] エンドユーザーに、ソリューションの証明書を信頼している組織全体のポリシーが存在しない場合は、信頼の決定を行うように求められます。 エンド ユーザーがソリューションに信頼を付与する場合は、この信頼の決定を格納するには、URL と公開キーを含む対象一覧のエントリが作成されます。 信頼されているカスタマイズの実行時、後で、エンドユーザーがもう一度メッセージが表示されません。

 管理者を無効にすることができます、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信頼プロンプトまたはの Authenticode 証明書で署名されているソリューションにのみ、プロンプトが発生することが必要です。 MyComputer、LocalIntranet、インターネット、しません、および UntrustedSites ゾーンの設定を変更する方法の詳細については、次を参照してください。[方法。ClickOnce 信頼プロンプトの動作を構成する](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)
- [ドキュメントに信頼を付与](../vsto/granting-trust-to-documents.md)
- [Office ソリューションのセキュリティをトラブルシューティングします。](../vsto/troubleshooting-office-solution-security.md)
- [Office ソリューションの特定のセキュリティに関する考慮事項](../vsto/specific-security-considerations-for-office-solutions.md)