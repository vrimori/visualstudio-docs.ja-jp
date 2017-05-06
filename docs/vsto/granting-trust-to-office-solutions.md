---
title: "Office ソリューションへの信頼の付与"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "セキュリティ [Visual Studio での Office 開発]、信頼"
  - "信頼のリスト [Visual Studio での Office 開発]、信頼のリストの概要"
  - "信頼 [Visual Studio での Office 開発]、2007 Office システム"
  - "付与 (信頼を) [Visual Studio での Office 開発]"
ms.assetid: 6c33e614-d367-4556-9e76-0f302ad0f929
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Office ソリューションへの信頼の付与
  Office ソリューションへの信頼の付与とは、ソリューション アセンブリ、アプリケーション マニフェスト、配置マニフェスト、およびドキュメントを信頼するように各ターゲット コンピューターのセキュリティ ポリシーを変更することを意味します。  信頼ユーザーまたはエンド ユーザーが Office ソリューションに付与できます。  
  
 Office ソリューションのアプリケーション マニフェストと配置マニフェストに署名して、完全に信頼を付与できます。  
  
 エンド ユーザーが Office ソリューションに [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] の信頼プロンプトの信頼の決定によって信頼を付与できます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> ソリューションのアプリケーション マニフェストと配置マニフェストの署名によって信頼します  
 Office ソリューションのすべてのアプリケーション マニフェストおよび配置マニフェストは、発行者を特定する証明書によって署名されている必要があります。  証明書は、信頼の決定を行う根拠となります。  
  
 ビルド時に一時的な証明書が自動的に作成され、信頼が付与されるため、デバッグ時にソリューションを実行できます。  一時的な証明書で署名されたソリューションを発行すると、エンド ユーザーが信頼の決定を求めるメッセージが表示されます。  
  
 ソリューションに既知の信頼された証明書で署名すると、そのソリューションはエンド ユーザーに信頼の決定を求めることなく自動的にインストールされます。  署名に使用する証明書を入手する方法の詳細については、「[ClickOnce と Authenticode](../deployment/clickonce-and-authenticode.md)」を参照してください。  証明書を入手したら、信頼された発行元の一覧に追加して、証明書を明示的に信頼する必要があります。  詳細については、「[方法 : ClickOnce アプリケーション用の信頼された発行者をクライアント コンピューターに追加する](../Topic/How%20to:%20Add%20a%20Trusted%20Publisher%20to%20a%20Client%20Computer%20for%20ClickOnce%20Applications.md)」を参照してください。  
  
 開発者がソリューションに一時的な証明書で署名した場合は、管理者が Microsoft .NET Framework ツールの 1 つであるマニフェストの生成および編集ツール \(mage.exe\) を使用して既知の信頼された証明書でカスタマイズに再署名できます。  ソリューションへの署名の詳細については、「[方法: Office ソリューションに署名する](../vsto/how-to-sign-office-solutions.md)」および「[方法 : アプリケーション マニフェストおよび配置マニフェストに署名する](../Topic/How%20to:%20Sign%20Application%20and%20Deployment%20Manifests.md)」を参照してください。  
  
##  <a name="TrustPrompt"></a> ソリューションの ClickOnce 信頼プロンプトを使用して信頼します  
 ソリューションの証明書を信頼する組織レベルのポリシーが存在しない場合、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] はエンド ユーザーに信頼の決定を要求します。  エンド ユーザーがソリューションに信頼を付与すると、URL と公開キーを含む信頼のリストのエントリが作成され、そこにユーザーによる信頼の決定が保存されます。  それ以降、信頼されたカスタマイズを実行すると、信頼の決定を求めるメッセージは表示されません。  
  
 管理者は、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信頼プロンプトを無効にしたり、Authenticode 証明書で署名されたソリューションについてのみ信頼プロンプトを表示したりできます。  これらの設定を MyComputer、LocalIntranet、Internet、TrustedSites、UntrustedSites の各ゾーンで変更する方法の詳細については、「[方法: ClickOnce 信頼プロンプトの動作を構成する](../Topic/How%20to:%20Configure%20the%20ClickOnce%20Trust%20Prompt%20Behavior.md)」を参照してください。  
  
## 参照  
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)   
 [ドキュメントへの信頼の付与](../vsto/granting-trust-to-documents.md)   
 [Office ソリューションのセキュリティのトラブルシューティング](../vsto/troubleshooting-office-solution-security.md)   
 [Office ソリューションに固有のセキュリティに関する考慮事項](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  