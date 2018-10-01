---
title: '例外のトラブルシューティング: System.ServiceModel.Security.MessageSecurityException |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: douge
ms.openlocfilehash: 9d886b8eeddc84c8b6597bca77e2d7b63ca21875
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548055"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>例外のトラブルシューティング : System.ServiceModel.Security.MessageSecurityException
A<xref:System.ServiceModel.Security.MessageSecurityException>ときに例外がスローされる[!INCLUDE[vsindigo](../includes/vsindigo-md.md)]メッセージが適切に保護されていないまたは改ざんされたことを決定します。 このエラーが最も発生しやすいのは、次の条件がすべて該当する場合です。  
  
-   リモート デスクトップ接続やターミナル サービスなどのリモート接続を介した WCF サービス参照を使用して、Web サイトまたは Web アプリケーション プロジェクト内の WCF サービス (.svc) と通信している。  
  
-   リモート サイトに管理者のアクセス許可がない。  
  
-   リモート サイトの localhost に対する要求が [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 開発サーバーによって処理されている。  
  
## <a name="associated-tips"></a>関連するヒント  
 **ASP.Net 開発サーバーを使用する場合は、NTLM 認証の問題を解決します。**  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 開発サーバーでは、通常、Windows NT チャレンジ/レスポンス (NTLM: Windows NT Challenge/Response) セキュリティがオフになっており、匿名アクセスが許可されています。 既定では、ターミナル サービス セッションを実行するか、リモート接続を使用すると、NTLM セキュリティが有効になります。 NTLM が有効である場合、すべての localhost 要求が [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 開発サーバーを起動したユーザーまたはプロセスの資格情報に対して検証されます。 これにより、セキュリティ上の脅威が軽減されます。 ただし、WCF は独自の認証も行い、管理者以外のアカウントに WCF サービスの利用を許可しません。  
  
 かどうか、リモート ユーザーを使用して Web サイトの実行可能性があります、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]開発サーバーもと協力し、Web サービスまたは WCF サービス、カスタム サービス バインディングを作成するか、NTLM セキュリティをオフにします。  
  
> [!IMPORTANT]
>  セキュリティが脆弱になる可能性があるため、NTLM セキュリティをオフにすることはお勧めしません。  
  
 カスタム サービス バインディングを作成した場合でも、引き続き NTLM 認証によって保護されます。  
  
 WCF サービスのカスタム サービス バインディングを作成するには、次の手順を実行します。  
  
#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>ASP.NET 開発サーバー内でホストされている WCF サービスのカスタム サービス バインディングを作成するには  
  
1.  例外が発生した WCF サービスの Web.config ファイルを開きます。  
  
2.  Web.config ファイルに次の情報を入力します。  
  
    ```  
    <bindings>  
      <customBinding>  
        <binding name="Service1Binding">  
          <transactionFlow />  
          <textMessageEncoding />  
          <httpTransport authenticationScheme="Ntlm" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
3.  Web.config ファイルを保存して閉じます。  
  
4.  WCF サービスまたは Web サービスのコードで、エンドポイント値を次のように変更します。  
  
    ```  
    <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
    ```  
  
     これにより、サービスがカスタム バインディングを使用するようになります。  
  
5.  サービスにアクセスする Web アプリケーションにサービスへの参照を追加します ( **[サービス参照の追加]** ダイアログ ボックスで、例外が発生した元のサービスで行ったようにサービスへの参照を追加します)。  
  
 WCF サービス参照を使用する場合に NTLM セキュリティをオフにするには、次の手順を実行します。  
  
> [!IMPORTANT]
>  セキュリティが脆弱になる可能性があるため、NTLM セキュリティをオフにすることはお勧めしません。  
  
#### <a name="to-turn-off-ntlm-security"></a>NTLM セキュリティをオフにするには  
  
1.  **[ソリューション エクスプローラー]** で Web サイト名を右クリックして、 **[プロパティ ページ]** をクリックします。  
  
2.  **[開始オプション]** をクリックし、 **[NTLM 認証]** チェック ボックスをオフにします。  
  
3.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [例外処理アシスタントを使用して、](http://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711)