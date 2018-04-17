---
title: Office ソリューションへの信頼の付与 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d3e89f9d864e80c3f3343b0d352105365e95e82
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="granting-trust-to-office-solutions"></a>Office ソリューションへの信頼の付与
  Office ソリューションへの信頼の付与は、ソリューション アセンブリ、アプリケーション マニフェスト、配置マニフェスト、およびドキュメントを信頼する場合は、各ターゲット コンピューターのセキュリティ ポリシーを変更することを意味します。 ユーザーまたはエンドユーザーによって、Office ソリューションに信頼を付与できます。  
  
 Office ソリューションに完全な信頼を付与するには、アプリケーション マニフェストと配置マニフェストに署名します。  
  
 エンドユーザーはで信頼の決定をすることにより、Office ソリューションに信頼を付与することができます、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信頼プロンプトです。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> マニフェストに署名アプリケーションおよび展開して、ソリューションを信頼します。  
 すべてのアプリケーションおよび配置マニフェストは for Office ソリューションは、パブリッシャーを識別する証明書で署名する必要があります。 証明書は、信頼性の決定を行うための基礎を提供します。  
  
 一時的な証明書が作成され、ソリューションをデバッグするときに実行するために、ビルド時に信頼を付与します。 一時的な証明書で署名されているソリューションを発行する場合は、信頼の決定にエンドユーザーが求められます。  
  
 既知の信頼された証明書を使用するソリューションをサインインしている場合、ソリューションは信頼の決定にエンド ユーザーに確認しないで自動的にインストールされます。 署名証明書を取得する方法の詳細については、次を参照してください。 [ClickOnce と Authenticode](/visualstudio/deployment/clickonce-and-authenticode)です。 証明書は、取得した後に、信頼された発行元一覧に追加して証明書を明示的に信頼する必要があります。 詳細については、「 [方法: ClickOnce アプリケーション用の信頼された発行者をクライアント コンピューターに追加する](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications)」を参照してください。  
  
 場合は、開発者は、一時的な証明書を使用するソリューションを署名、管理者が再署名既知の信頼された証明書を指定してカスタマイズ マニフェストの生成とは、Microsoft .NET Framework ツールのいずれかの編集のツール (mage.exe) を使用しています。 ソリューションの署名の詳細については、次を参照してください。[する方法: Office ソリューションの記号](../vsto/how-to-sign-office-solutions.md)と[する方法: 符号アプリケーション マニフェストと配置マニフェスト](/visualstudio/ide/how-to-sign-application-and-deployment-manifests)です。  
  
##  <a name="TrustPrompt"></a> ClickOnce 信頼プロンプトを使用して、ソリューションを信頼します。  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] ソリューションの証明書を信頼している組織全体のポリシーが存在しない場合は、信頼の決定を行うには、エンドユーザーのメッセージを表示します。 ソリューションに信頼を付与すると、エンドユーザーがユーザーの場合は、この信頼の決定を格納するには、URL と公開キーを含む信頼のリストのエントリが作成されます。 実行すると、信頼されたカスタマイズが後で、エンド ユーザーは再度プロンプトされません。  
  
 管理者が無効にすることができます、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]信頼プロンプトまたはの Authenticode 証明書で署名されているソリューションにのみ、プロンプトが発生することが必要です。 MyComputer、ローカル イントラネット、インターネット、しません、および UntrustedSites ゾーンに対するこれらの設定を変更する方法の詳細については、次を参照してください。[する方法: ClickOnce 信頼プロンプト動作を構成する](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior)です。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)   
 [ドキュメントへの信頼の付与](../vsto/granting-trust-to-documents.md)   
 [Office ソリューションのセキュリティのトラブルシューティング](../vsto/troubleshooting-office-solution-security.md)   
 [Office ソリューションに固有のセキュリティに関する考慮事項](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  